<template>
    <div class="container">
        <div class="row">
            <div class="col-md-8 col-md-offset-2">
                <div class="panel panel-default">
                    <div class="panel-heading"><h4>All Articles</h4></div>
                    <div class="panel-body">
                       <ul class="list-group">
                            <li v-if='list.length === 0'>There are no tasks yet!</li>
                            <li class="list-group-item" v-for="(task, index) in list">
                                {{ task.id }} {{ task.body }}
                            </li>
                       </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        mounted() {
            console.log('Article List mounted.')
        },

        ready() {
            this.fetchArticlesList()
        },

        data() {
            return {
                list: [],
                task: {
                    id: '',
                    body: ''
                }
            };
        },

        methods: {
            fetchArticlesList() {
                axios.get('api/articles').then((res) => {
                    this.list = res.data;
                });
            },
        }
    }
</script>
