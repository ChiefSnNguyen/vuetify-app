<template>
    <div class="projects">
        <h1 class="subheading grey--text">Project</h1>
        <v-container>
            <v-layout row wrap class="mb-4">
                <v-tooltip bottom>
                    <template v-slot:activate="{ on }">
                        <v-btn small outlined color="green" @click="sortBy('title')" class="mr-2" dark v-on="on">
                            <v-icon left small>folder</v-icon>
                            <span class="caption text-lowercase">By project title</span>
                        </v-btn>
                    </template>
                    <span>sort project</span>
                </v-tooltip>
                <v-tooltip bottom>
                    <template v-slot:activate="{ on }">
                        <v-btn small outlined color="green" @click="sortBy('title')" class="mr-2" dark v-on="on">
                            <v-icon left small>person</v-icon>
                            <span class="caption text-lowercase">By name</span>
                        </v-btn>
                    </template>
                    <span>sort person</span>
                </v-tooltip>
            </v-layout>
            <v-card flat v-for="project in projects" :key="project.title" class="mb-1">
                <v-layout row wrap :class="`pa-3 project ${project.status}`">
                    <v-flex xs12 md6>
                        <div class="caption grey--text">Person</div>
                        <div>{{project.person}}</div>
                    </v-flex>
                    <v-flex xs-6 sm4 md2>
                        <div class="caption grey--text">Due by</div>
                        <div>{{project.due}}</div>
                    </v-flex>
                </v-layout>
            </v-card>
        </v-container>
    </div>
</template>

<script>
export default {
    data: () => ({
        projects: [
            {tilte: 'SiteWeb', person: 'Khaleb', due:'10/10/1987', status: 'complete'},
            {tilte: 'Application Mobile', person: 'Iyad', due:'02/07/1990', status: 'complete'},
            {tilte: 'Gestion de stock', person: 'Zineb', due:'01/05/1987', status: 'yes'},
            {tilte: 'Conception', person: 'Hu Java', due:'02/09/1991', status: 'up'},
        ]
    }),
    methods: {
        sortBy(prop){
            this.projects.sort((a, b) => a[prop] < b[prop] ? -1 : 1)
        }
    }
}
</script>

<style>
.project.complete {
    border-left: 4px solid #3cd1c2;
}
.project.no {
    border-left: 4px solid orange;
}
.project.up {
    border-left: 4px solid red;
}
.project.yes {
    border-left: 4px solid yellow;
}
</style>