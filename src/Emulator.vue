<template>
    <div>
        <div id="editor-and-registers">
            <div class="editor-container">
                <textarea id="editor" cols="30" rows="10" spellcheck="false">{{ asm }}
                </textarea>
            </div>
            <div class="registers-container">
                <table class="registers">
                    <tr class>
                        <td class="register-labels">PC</td>
                        <td class="register-values">0x0000</td>
                    </tr>
                    <tr>
                        <td class="register-labels">SP</td>
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
        <div class="page-controller-container">
            <div class="page-controller">
                <button class="buttons" id="run-button" v-on:click="returnPages(16)">&lt&lt</button>
                <button class="buttons" v-on:click="returnPages(1)">&lt</button>
                <div>{{ this.formattedPage }}</div>
                <button class="buttons" v-on:click="skipPages(1)">></button>
                <button class="buttons" id="run-button" v-on:click="skipPages(16)">>></button>
            </div>
        </div>
        <div class="memory-container">
            <table id="memory">
                <tr v-for="row in memory">
                    <td
                        v-for="(cell, index) in row"
                        :class="[index ==
                        0 ? rowIndexClass : 'dataCell']"
                    >
                        {{
                            cell.toString(16).padStart(2,
                                '0').toUpperCase()
                        }}
                    </td>
                </tr>
            </table>
        </div>
    </div>
</template>
<script>

let asm = "LDY #$01\nLDA #$03\nSTA $01\nLDA #$07\nSTA $02\nLDX #$0a\nSTX $0704\nLDA($01), Y\n";

export default {
    data() {
        let filas = 16;
        let columnas = 17;
        let memory = new Array(filas);
        for (let i = 0; i < filas; i++) {
            memory[i] = new Array(columnas);
            memory[i][0] = i * 0x10;
            for (let j = 1; j < columnas; j++) {
                memory[i][j] = i % j;
            }
        }
        return {
            memory,
            rowIndexClass: 'mem-row-index',
            page: 0,
            asm
        }
    },
    computed: {
        formattedPage() {
            return "0x" + this.page.toString(16).padStart(2,
                '0').toUpperCase()
        }
    },
    methods: {
        skipPages(num) {
            if (this.page + num < 256) {
                this.page += num;
            }
        },
        returnPages(num) {
            if (this.page - num > -1) {
                this.page -= num;
            }
        }

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
    height: 312px;
    resize: none;
    font-size: 20px;
    font-family: Iosevka;
}

#editor-and-registers {
    margin: 0 auto;
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
    width: 100px;
    display: inline-block;
}
.editor-container {
    width: 250px;
    max-width: 250px;
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

.red-next-button {
    background-color: #ff353c;
    color: black;
}

#console {
    width: 100%;
    height: 100px;
    background-color: black;
    font-size: 20px;
    color: #00ff0c;
    margin-top: 20px;
    display: inline-block;
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

.memory-container {
    padding-top: 10px;
    font-family: Iosevka;
    font-size: 25px;
    color: #292929;
}

table#memory {
    border-collapse: collapse;
}

table#memory > tr > td {
    padding-left: 10px;
    padding-right: 10px;
    padding-top: 0px;
}

.mem-row-index {
    background-color: #737373;
}

.dataCell {
    background-color: #cfcfcf;
}

.page-controller {
    padding-top: 10px;
    display: inline-block;
    margin: 0 auto;
}

.page-controller > div {
    display: inline-block;
    border: 2px solid white;
    color: black;
    background-color: #e6e6e6;
    text-decoration: none;
    font-family: Iosevka;
    font-size: 35px;
    padding-left: 10px;
    padding-right: 10px;
    margin-left: 10px;
    margin-right: 10px;
}

.page-controller-container {
    text-align: center;
}
</style>
