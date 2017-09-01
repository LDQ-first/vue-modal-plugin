<template>
    <div class="show">
        <header>
            <h1>Vue Modal Plugin</h1>
        </header>
        <article>
            <section class="section-first">
                <div class="ui">
                    <h2>Use</h2>
                    <p class="remind">
                         <span class="keypoint">
                            <img class="remind-img" src="../assets/icon/resume.svg">
                            <strong>You should restart vue after finishing install vue-usemodal</strong>
                        </span>
                        <span>
                            Ripple isn't necessary
                        </span>
                    </p>
                </div>
                <div class="code" v-hljs>
                    <pre><code>{{codeFirst.npm}}</code></pre>
                    <pre><code>{{codeFirst.js}}</code></pre>
                </div>
            </section>
            <section class="section-one">
                <div class="ui">
                    <h2>Modal One</h2>
                    <ripple class="ripbtn" :isInline="isInline">
                        <button slot="pure" @click="showMoal('one')">showModal</button>
                    </ripple>
                </div>
                <div class="code" v-hljs>
                    <pre><code>{{codeOne.html}}</code></pre>
                </div>
            </section>
            <section class="section-two">
                <div class="ui">
                    <h2>Modal Two</h2>
                    <ripple class="ripbtn" :isInline="isInline">
                        <button slot="pure" @click="showMoal('two')">showModal</button>
                    </ripple>
                </div>
                <div class="code" v-hljs>
                    <pre><code>{{codeTwo.html}}</code></pre>
                </div>
            </section>
            <section class="section-three">
                <div class="ui">
                    <h2>Modal Three</h2>
                    <ripple class="ripbtn" :isInline="isInline">
                        <button slot="pure" @click="showMoal('three')">showModal</button>
                    </ripple>
                </div>
                <div class="code" v-hljs>
                    <pre><code>{{codeThree.html}}</code></pre>
                </div>
            </section>
            <section class="section-four">
                <div class="ui">
                    <h2>Modal Four</h2>
                    <ripple class="ripbtn">
                        <div slot="pure" class="panel" :style="{background: `${bg}`}">
                            <header>
                                <h3>This is a panel</h3>
                            </header>
                            <div class="content">
                                <p>Its backgroundColor is {{bg}}</p>
                            </div>
                        </div>
                    </ripple>
                    <ripple class="ripbtn" :isInline="isInline">
                        <button slot="pure" @click="showMoal('four')">showModal</button>
                    </ripple>
                </div>
                <div class="code" v-hljs>
                    <pre><code>{{codeFour.html}}</code></pre>
                    <pre><code>{{codeFour.css}}</code></pre>
                </div>
            </section>
        </article>
        <footer>
            <p>Copyright {{copyRightYear}} © by <a href="https://github.com/LDQ-first">LDQ-first</a> (◕ᴗ◕)</p>
            <p>
                demo source code in Github => 
                <a href="https://github.com/LDQ-first/vue-modal-plugin" title="click me">
                    <img class="github-img" src="../assets/icon/github.svg" >
                </a>
            </p>
            <p>
                vue plugin source code in Github => 
                <a href="https://github.com/LDQ-first/vue-usemodal" title="click me">
                    <img class="github-img" src="../assets/icon/github.svg" >
                </a>
            </p>
        </footer>
        <modal :mdShow="modalOne" @close="closeModal('one')">
            <h3 slot="title" class="">Modal One</h3>
        </modal>
        <modal :mdShow="modalTwo" @close="closeModal('two')">
            <h3 slot="title" class="">Modal Two</h3>
            <p slot="message">
                {{modalMessage}}
            </p>
        </modal>
        <modal :mdShow="modalThree" @close="closeModal('three')">
            <h3 slot="title" class="">Modal Three</h3>
            <p slot="message">
                {{modalMessage}}
            </p>
            <div slot="btnGroup" class="btnGroup">
                <button class="md-close" @click="closeModal('three')">closeModal</button>
            </div>
        </modal>
        <modal :mdShow="modalFour" @close="closeModal('four')">
            <h3 slot="title" class="">Modal Four</h3>
            <p slot="message">
                {{modalMessage}}
            </p>
            <div slot="btnGroup" class="btnGroup">
                <button class="md-close" @click="changeBg();closeModal('four')">sure</button>
                <button class="md-close" @click="closeModal('four')">cancel</button>
            </div>
        </modal>
    </div>
</template>

<script>
    const Modal = resolve => require(['../components/modal.vue'], resolve)
    
    export default {
        data () { 
            return {
                codeFirst: {
                    npm: '',
                    js: ''
                },
                copyRightYear: '',
                modalOne: false,
                modalTwo: false,
                modalThree: false,
                modalFour: false,
                modalFive: false,
                modalMessage: 'This is a Modal',
                isInline: true,
                br: true,
                bg: '#50CCD3',
                codeOne: {
                    html: ''
                },
                codeTwo: {
                    html: ''
                },
                codeThree: {
                    html: ''
                },
                codeFour: {
                    html: '',
                    css: ''
                },
            }
        },
        components: {
            Modal
        },
        created () {
            this.setCode()
            this.setYear()
        },
        methods: {
            showMoal (num) {
                this.setModalMessage(num)
                switch (num) {
                    case 'one':
                      this.modalOne = true
                      break;
                    case 'two':
                      this.modalTwo = true
                      break;
                    case 'three':
                      this.modalThree = true
                      break;
                    case 'four':
                      this.modalFour = true
                      break;
                }
            },
            closeModal (num) {
                switch (num) {
                    case 'one':
                      this.modalOne = false
                      break;
                    case 'two':
                      this.modalTwo = false
                      break;
                    case 'three':
                      this.modalThree = false
                      break;
                    case 'four':
                      this.modalFour = false
                      break;
                }
            },
            setModalMessage (num) {
                switch (num) {
                    case 'one':
                      this.modalMessage = 'This is a Modal One'
                      break;
                    case 'two':
                      this.modalMessage = 'This is a Modal Two'
                      break;
                    case 'three':
                      this.modalMessage = 'This is a Modal Three'
                      break;
                    case 'four':
                      this.modalFour = 'This is a Modal Four'
                      break;
                }
            },
            changeBg () {
                this.bg = this.bg === '#50CCD3' ? '#F18E5B' : '#50CCD3'
            },
            setYear () {
                const year = new Date().getFullYear()
                if(year === 2017) {
                     this.copyRightYear = 2017
                } else {
                    this.copyRightYear = 2017 + ' - ' + year
                }
                
            },
            setCode () {
                this.codeFirst.npm =
    `
    /*-- npm --*/
    npm install --save vue-usemodal

    `
                    this.codeFirst.js = 
    `
    /*-- main.js --*/
    import Vue from 'vue'
    import VueRipple from 'vue-usemodal'
    Vue.use(VueRipple)
    `
                    this.codeOne.html = 
    ` 
    <!--html-->
    <modal :mdShow="modalOne" @close="closeModal('one')">
        <h3 slot="title" class="">Modal One</h3>
    </modal>
    `
                    this.codeTwo.html =
    `
    <!--html-->
    <div class="ui">
        <h2>Modal Two</h2>
        <ripple class="ripbtn" :isInline="isInline">
            <button slot="pure" @click="showMoal('two')">showModal</button>
        </ripple>
    </div>
    `
                this.codeThree.html = 
    `
    <!--html-->
     <div class="ui">
        <h2>Modal Three</h2>
        <ripple class="ripbtn" :isInline="isInline">
            <button slot="pure" @click="showMoal('three')">showModal</button>
        </ripple>
    </div>
    `
               
                this.codeFour.html = 
    `
    <!--html-->
    <modal :mdShow="modalFour" @close="closeModal('four')">
        <h3 slot="title" class="">Modal Four</h3>
        <p slot="message">
            {{modalMessage}}
        </p>
        <div slot="btnGroup" class="btnGroup">
            <button class="md-close" @click="changeBg();closeModal('four')">sure</button>
            <button class="md-close" @click="closeModal('four')">cancel</button>
        </div>
    </modal>
    
    `
                this.codeFour.css = 
    `
    /*-- sass --*/
    .btnGroup {
        display: flex;
        justify-content: space-around;
        margin: 20px 0;
    }
     @mixin panel {
        border: 2px solid #8BE388; 
        padding: 20px;
        background: #EEE;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        header {
            width: 100%;
            text-align: left;
        } 
        .content {
            margin: 20px 0;
        }
    }
    .section-four {
        .ripPanel.rippleWrapper {
            width: 80%;
            max-width: 800px;
            margin: 20px auto;
        }
        .panel {
             @include panel
        }
        .br {
            width: 88px;
            height: 88px;
        }
        .des {
            margin: 0 10px;
        }
    }
    `

                
                  
            }

        }
     }
</script>

<style lang="scss" scoped>
    h1, h2, h3, p{
        margin: 10px 0;
    }
    section, footer {
        margin: 50px 0;
    }
    strong {
        margin: 0 20px;
    }
    .remind {
        width: 80%;
        max-width: 800px;
        margin: 20px auto;
        border: 2px solid #8BE388; 
        padding: 20px 0;
        background: #EEE;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        span {
            margin: 10px 0;
        }
        .keypoint  {
            .remind-img {
                margin: 0 20px;
                vertical-align: middle;
            }
        }
        
    } 
    .github-img {
        width: 30px;
        vertical-align: bottom;
        margin: 0 10px;
        animation: sway 2s ease-in-out infinite alternate;
        transform-origin: 50% 100%;
    }
    @keyframes sway {
        0% {
            transform: rotate(-35deg)
        }
        100% {
            transform: rotate(35deg)
        }
    }
    .ripbtn {
        margin: 12px;
    }
    .code {
        width: 80%;
        max-width: 768px;
        margin: 0 auto;
    }
    .btnGroup {
        display: flex;
        justify-content: space-around;
        margin: 20px 0;
    }
     @mixin panel {
        border: 2px solid #8BE388; 
        padding: 20px;
        background: #EEE;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        header {
            width: 100%;
            text-align: left;
        } 
        .content {
            margin: 20px 0;
        }
    }
    .section-four {
        .ripPanel.rippleWrapper {
            width: 80%;
            max-width: 800px;
            margin: 20px auto;
        }
        .panel {
             @include panel
        }
        .br {
            width: 88px;
            height: 88px;
        }
        .des {
            margin: 0 10px;
        }
    }
    
</style>
