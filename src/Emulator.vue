<template>
    <div>
        <div id="editor-and-registers">
            <textarea id="editor" cols="30" rows="10"></textarea>
            <div id="registers">PC X Y</div>
        </div>
    </div>
</template>
<script>

export default {
    data() {
        return {}
    }
}
</script>

<style>
#editor {
    width: 250px;
    height: 300px;
    resize: none;
    font-size: 20px;
    float: left;
}
#registers {
    float: right;
    font-family: Consolas, sans-serif;
    font-size: 25px;
    margin: 10px;
}
</style>
