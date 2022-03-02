<template>
    <div>
        <div id="editor-and-registers">
            <div class="editor-container">
                <textarea id="editor" cols="30" rows="10"
                spellcheck="false">
LDY #$01
LDA #$03
STA $01
LDA #$07
STA $02
LDX #$0a
STX $0704
LDA ($01),Y
                </textarea>
            </div>
            <div class="registers-container">
                <table class="registers">
                    <tr class="register-labels">
                        <td class="pc">PC</td>
                        <td class="x">X</td>
                        <td class="y">Y</td>
                    </tr>
                    <tr class="register-values">
                        <td class="pc">0x0000</td>
                        <td class="x">0x00</td>
                        <td class="y">0x00</td>
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
    font-family: Fixedsys;
    /* float: left; */
    /* overflow: auto; */
}

.registers {
    font-family: Fixedsys;
    font-size: 35px;
    line-height:30px ;
    color: #1f1f1f;
}
.register-labels {
    text-align: left;
    color:#393939;
}
.status-register-labels {
    text-align: center;
}
.register-values {
    border-collapse: collapse;
}

.registers-container {
    padding-left: 10px;
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
/* td, table{ */
    /* border: 2px solid black; */
    /* border-collapse: collapse; */
/* } */

.pc {
    color: #ff3a42;
}

.x{
    color: #00ff44;
}

.y{
     color: #002dff;
}
</style>
