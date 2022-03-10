<template>
    <div>
        <div id="editor-and-registers">
            <div class="editor-container">
                <textarea id="editor" cols="30" rows="10" spellcheck="false">
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
                    <tr class>
                        <td class="register-labels">PC</td>
                        <td class="register-values">0x0000</td>
                    </tr>
                    <tr>
                        <td class="register-labels">X</td>
                        <td class="register-values">0xF3</td>
                    </tr>
                    <tr>
                        <td class="register-labels">Y</td>
                        <td class="register-values">0x00</td>
                    </tr>
                    <tr>
                        <td class="register-labels">AC</td>
                        <td class="register-values">0x00</td>
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
                <table class="buttons-container">
                    <tr>
                        <td>
                            <button class="buttons" id="run-button">Run</button>
                        </td>
                        <td>
                            <button class="buttons" id>Reset</button>
                        </td>
                    </tr>
                </table>
            </div>
        </div>
        <div id="console">Compilation succesful.</div>
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

@font-face {
    font-family: "Iosevka";
    src: local("Fixedsys"),
        url(./fonts/iosevka-term-ss18-regular.ttf) format("truetype");
}

#editor {
    width: 250px;
    height: 300px;
    resize: none;
    font-size: 20px;
    font-family: Iosevka;
}

.registers {
    font-family: Fixedsys;
    font-size: 35px;
    line-height: 30px;
    color: #1f1f1f;
}
.register-labels {
    text-align: left;
}
.status-register-labels {
    text-align: center;
}
.register-values {
    border-collapse: collapse;
    text-align: right;
    color: #727272;
}

.registers-container {
    padding-left: 10px;
    float: right;
    width: 100px;
    /* display: inline-block; */
}
.editor-container {
    /* float: left; */
    width: 250px;
    max-width: 250px;
    /* overflow: auto; */
    /* display: inline-block; */
    float: left;
}
.pc {
    color: #ff3a42;
}
.x {
    color: #00ff44;
}
.y {
    color: #002dff;
}
.buttons {
    border: 2px solid white;
    text-decoration: none;
    font-family: Iosevka;
    font-size: 35px;
}

#run-button:hover {
    border: 2px solid black;
}

#run-button {
    background-color: #ff353c;
    color: white;
}

#console {
    width: 100%;
    height: 100px;
    background-color: black;
    font-size: 20px;
    color: #00ff0c;
    margin-top: 20px;
    display: inline-block;
    /* float: left; */
    /* font-family: Fixedsys; */
    font-family: Iosevka;
}

@-webkit-keyframes blink {
    0% {
        opacity: 1;
    }
    50% {
        opacity: 0;
    }
    100% {
        opacity: 1;
    }
}

@keyframes blink {
    0% {
        opacity: 1;
    }
    50% {
        opacity: 0;
    }
    100% {
        opacity: 1;
    }
}

.buttons-container {
    padding-top: 20px;
}
</style>
