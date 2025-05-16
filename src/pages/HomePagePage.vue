<template>
    <div class="new">
        <a href="#ajouter" style="margin: 5px;">Nouvelle Tache</a>
    </div>
    <div class="container ">
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Tâches</th>
                    <th scope="col">Date</th>
                    <th scope="col">Statut</th>
                    <th scope="col">Action</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th scope="row">1</th>
                    <td>Mark</td>
                    <td>Otto</td>
                    <td>@mdo</td>
                    <td>@mdo</td>
                </tr>
                <tr>
                    <th scope="row">2</th>
                    <td>Jacob</td>
                    <td>Thornton</td>
                    <td>@fat</td>
                    <td>@fat</td>
                </tr>
                <tr>
                    <th scope="row">3</th>
                    <td>John</td>
                    <td>Doe</td>
                    <td>@fat</td>
                    <td>@social</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script setup>
</script>

<style>
.table {
    margin-top: 2rem;
}

.new {
    margin-top: 2rem;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}

.new a {
    border: 0.15rem rgba(104, 104, 220, 0.789) solid;
    border-radius: 1rem;
    padding: 1rem;
    color: blue;
}

.new a:hover {
    border-radius: 1rem;
    background-color: rgba(104, 104, 220, 0.789);
    padding: 1rem;
    color: wheat;
}
</style>