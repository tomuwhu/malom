<style scoped>
    #base {
        text-align: center;
    }
    table {
        border-collapse: inherit;
    }
    td {
        font-size: 26px;
        text-align: center;
    }
    td.d1 {
        box-shadow: 0px 0px 3px black;
        border-color: rgb(150, 133, 111);
        border-radius: 18px;
        border: solid 2px black;
        width: 30px;
        height: 30px;
    }
    td.d2 {
        width: 30px;
        height: 30px;
        
    }
    td.d3{
        width: 30px;
        height: 30px;
    }
    div.O {
        margin: 4px auto;
        border-radius: 18px;
        width: 20px;
        height: 20px;
        cursor: pointer;
    }
    div.Empty {
        width: 20px;
        height: 20px;
    }
    div.R {
        background-color: rgb(194, 28, 28);
        box-shadow: 0px 0px 5px black;
    }
    div.B {
        background-color: rgb(69, 28, 194);
        box-shadow: 0px 0px 5px black;
    }
</style>

<template>
    <div id="base">
        <br>
        <br>
        <table style="margin: 0 auto;">
            <tr :key="y" v-for="(row,y) in table">
                <td :key="x" v-for="(cell,x) in row" :class="'d'+cell">
                    <div class="Empty" v-if="cell=='0'" />
                    <div class="O R" v-if="cell=='R' || szin(x,y,'R')" />
                    <div class="O B" v-if="cell=='B' || szin(x,y,'B')" />
                    <div class="O" v-if="count<18 && szin(x,y,'0')" @click="katt(x,y)" />
                    <span v-if="cell=='2'">
                        |
                    </span>
                    <span v-if="cell=='3'">
                        ---
                    </span>
                </td>
            </tr>
        </table>
    </div>
</template>
 
<script>
export default {
    data: () => ({
        table: [
                [1,3,3,3,3,3,1,3,3,3,3,3,1],
                [2,0,0,0,0,0,2,0,0,0,0,0,2],
                [2,0,1,3,3,3,1,3,3,3,1,0,2],
                [2,0,2,0,0,0,2,0,0,0,2,0,2],
                [2,0,2,0,1,3,1,3,1,0,2,0,2],
                [2,0,2,0,2,0,0,0,2,0,2,0,2],
                [1,3,1,3,1,0,0,0,1,3,1,3,1],
                [2,0,2,0,2,0,0,0,2,0,2,0,2],
                [2,0,2,0,1,3,1,3,1,0,2,0,2],
                [2,0,2,0,0,0,2,0,0,0,2,0,2],
                [2,0,1,3,3,3,1,3,3,3,1,0,2],
                [2,0,0,0,0,0,2,0,0,0,0,0,2],
                [1,3,3,3,3,3,1,3,3,3,3,3,1],
                [0,0,0,0,0,0,0,0,0,0,0,0,0],
                ['R','R','R','R','R','R','R','R','R',0,0,0,0],
                [0,0,0,0,'B','B','B','B','B','B','B','B','B'],
        ],
        Rf: new Set,
        Bf: new Set,
        next: 'R',
        count: 0
    }),
    methods: {
        szin(x,y,szin) {
            if (szin=='0') {
                return  !this.Rf.has(`${x}-${y}`) && 
                        !this.Bf.has(`${x}-${y}`) && 
                         this.table[x][y]===1
            } else {
                let check
                if (szin=='R')         
                    check=this.Rf
                if (szin=='B')  
                    check=this.Bf
                return check.has(`${x}-${y}`)
            }           
        },
        katt(x,y) {
            let toadd
            if (this.next=='R') toadd=this.Rf
            else toadd=this.Bf
            toadd.add(`${x}-${y}`)            
            if (this.next=='B')
                this.$set(this.table[15],12-this.count++/2+0.5,0)
            else 
                this.$set(this.table[14],this.count++/2,0)
            this.next=this.next=='R'?'B':'R'
        }
    }
}
</script>
