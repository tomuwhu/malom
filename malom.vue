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
</style>

<template>
    <div id="base">
        <br>
        <br>
        <table style="margin: 0 auto;">
            <tr :key="y" v-for="(row,y) in table">
                <td :key="x" v-for="(cell,x) in row" :class="'d'+cell">
                    <div class="RO" v-if="cell=='1'">
                        O
                    </div>
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
                [1,3,3,3,3,3,1,3,3,3,3,3,1]
        ]
    })
}
</script>
