<template>
    <div class="contenedor">
        <h2>Calculadora</h2>

        <div class="pantalla">
            {{ (pantalla || '0').replaceAll('*', 'X')}}
        </div>

        <div class="botones">
            <button @click="memoriaArriba">↑</button>
            <button @click="memoriaAbajo">↓</button>
            <button @click="limpiar">AC</button>
            <button @click="borrar">CE</button>
    
            <button @click="agregar('7')">7</button>
            <button @click="agregar('8')">8</button>
            <button @click="agregar('9')">9</button>
            <button @click="agregar('/')">/</button>

            <button @click="agregar('4')">4</button>
            <button @click="agregar('5')">5</button>
            <button @click="agregar('6')">6</button>
            <button @click="agregar('*')">X</button>

            <button @click="agregar('1')">1</button>
            <button @click="agregar('2')">2</button>
            <button @click="agregar('3')">3</button>
            <button @click="agregar('-')">-</button>

            <button @click="agregar('0')">0</button>
            <button @click="agregar('.')">.</button>
            <button @click="calcular">=</button>
            <button @click="agregar('+')">+</button>
        </div>
    </div>
</template>
<script>
import { evaluate } from 'mathjs'

export default {
    data() {
        return {
            pantalla: '',
            memoria: [],
            indiceMemoria: 0
        }
    },

    methods: {
        agregar(valor) {
            if(this.pantalla === 'E') {
                this.pantalla = '';
            }
            if (this.pantalla.length >= 10) {
                return;
            }
            const ultimo = this.pantalla[this.pantalla.length -1]
            const operadores = ['+', '-', '*', '/']

            if (operadores.includes(valor)) {
                if (this.pantalla === '' && valor !== '-') {
                    return
                }
                

                if (operadores.includes(ultimo)) {
                    if (valor === '-' && ultimo !== '-') {
                        this.pantalla += valor
                    }
                    return
                }
            }
            this.pantalla += valor
        },
    
        calcular() {
            if (this.pantalla === '') {
                return
            }

            if (this.pantalla === '0*1') {
                this.pantalla = '1111111111'
                this.guardarMemoria(this.pantalla)
                return
            }

            const codigo = this.buscarCodigoEspecial(this.pantalla)

            if (codigo) {
                this.pantalla = codigo
                this.guardarMemoria(codigo)
                return
            }

            try {
                const resultado = evaluate(this.pantalla)

                if(!isFinite(resultado)) {
                    this.pantalla = 'E'
                    return
                }

                const texto = String(resultado)

                if (texto.length > 10) {
                    this.pantalla = 'E'
                    return
                }

                this.pantalla = texto
                this.guardarMemoria(texto)

            }catch (error) {
                this.pantalla = 'E'
            }
        },

        buscarCodigoEspecial(valor) {
            const codigosEspeciales = {
                '705': 'SOL',
                '15': 'SI',
                '505': 'SOS',
                '310': 'OIE',
                '037': 'LEO',
                '053': 'ESO',
                '080': 'OBO',
                '0705': 'SOLO',
                '5135': 'SEIS',
                '3838': 'BEBE',
                '50538': 'BESOS',
                '50535': 'SESOS',
                '50807': 'LOBOS',
                '50735': 'SELOS',
                '01838': 'BEBIO',
                '376006': 'GOOGLE',
                '5135135': 'SEISEIS',
                
                '07734': 'HELLO',
                '5318008': 'BOOBIES',
                '53045': 'SHOES',
                '35006': 'GOOSE',
                '376606': 'GOGGLE',
                '3735': 'SELE',
                '37818': 'BIBLE',
                '0637': 'LEGO',
                '5317': 'LIES',
                '3507': 'LOSE',
                '35007': 'LOOSE',
                '58008': 'BOOBS',
                '7734': 'HELL',
                '35336': 'GEESE',
                '3507318': 'BIE LOSE',
                '0773405': 'SO HELLO',
            }

            return codigosEspeciales[valor] || null
        },

        guardarMemoria(resultado) {
            this.memoria.push(resultado)
            if (this.memoria.length > 15) {
                this.memoria.shift()
            }
            this.indiceMemoria = this.memoria.length 
        },

        memoriaArriba() {
            if (this.memoria.length === 0) {
                return
            }
            if (this.indiceMemoria > 0) {
                this.indiceMemoria--
            }
            this.pantalla = this.memoria[this.indiceMemoria]
        },
        memoriaAbajo() {
            if (this.memoria.length === 0) {
                return
            }
            if (this.indiceMemoria < this.memoria.length - 1) {
                this.indiceMemoria++
                this.pantalla = this.memoria[this.indiceMemoria]
            }else {
                this.indiceMemoria = this.memoria.length
                this.pantalla = ''
            }
        },
        limpiar() {
            this.pantalla = ''
        },
        borrar() {
            if (this.pantalla.length > 0) {
                this.pantalla = this.pantalla.slice(0, -1)
            }
        }
    }    
}

</script>

<style scoped>
.contenedor {
    width: 260px;
    margin: 40px auto;
    font-family: Arial, sans-serif;
}

.pantalla {
    height: 45px;
    border: 1px solid black;
    margin-bottom: 10px;
    font-size: 25px;
    text-align: right;
    line-height: 45px;
}

.botones {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 6px;
}

button {
    height: 45px;
    font-size: 18px;
    cursor:pointer;
}

</style>