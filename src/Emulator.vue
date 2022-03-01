<template>
    <div>
        <div id="editor-and-registers">
            <div class="editor-container">
                <textarea id="editor" cols="30" rows="10"></textarea>
            </div>
            <div class="registers-container">
                <table class="registers">
                    <tr class="register-labels">
                        <td class="pc">PC</td>
                        <td>X</td>
                        <td>Y</td>
                    </tr>
                    <tr class="register-values">
                        <td class="pc">0x00</td>
                        <td>0x00</td>
                        <td>0x00</td>
                    </tr>
                </table>
                <table class="registers">
                    <tr class="status-register-labels">
                        <td>N</td>
                        <td>V</td>
                        <td>-</td>
                        <td>B</td>
                        <td>D</td>
                        <td>I</td>
                        <td>Z</td>
                        <td>C</td>
                    </tr>
                    <tr class="register-values">
                        <td>0</td>
                        <td>0</td>
                        <td>0</td>
                        <td>0</td>
                        <td>0</td>
                        <td>0</td>
                        <td>0</td>
                        <td>0</td>
                    </tr>
                </table>
            </div>
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
@font-face {
    font-family: "Fixedsys";
    src: local("Fixedsys"), url(./fonts/FSEX302.ttf) format("truetype");
}

#editor {
    width: 250px;
    height: 300px;
    resize: none;
    font-size: 20px;
    /* float: left; */
    /* overflow: auto; */
}

.registers {
    font-family: Fixedsys;
    font-size: 35px;
}
.register-labels {
    text-align: left;
    margin-bottom: 0px;
    padding-bottom: 0px;
}
.status-register-labels {
    text-align: center;
}
.register-values > td {
    margin-top: 0px;
    padding-top: 0px;
}

.registers-container {
    padding-left: 1px;
    float: right;
    width: 100px;
    display: inline;
}
.editor-container {
    /* float: left; */
    width: 250px;
    max-width: 250px;
    /* overflow: auto; */
    /* display: inline; */
    float: left;
}

.pc {
}
</style>
