<template>
    <div class="col-sm-6 col-md-4 col-lg-3">
        <div class="panel panel-default quote">
            <slot></slot>
        </div>
    </div>
</template>

<style>
    .quote {
        cursor: pointer;
        font-family: cursive;
        font-size: 24px;
        padding:30px
    }
    .quote:hover {
        background-color: #ffe2e2 
    }
</style>
