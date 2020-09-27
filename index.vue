<template>
    <div>
        Home
        <V1 @onV1Msg="v1MsgHandler"/>
        <V2 :v2Msg="v2Msg"/>
        <hr />
        <div>
            <button @click="AddHandler">增肌1</button>
            <button @click="ReduceHandler">减少</button>
        </div>
        <hr />
        <V3 />
    </div>
</template>

<script>
import V1 from "../../components/V1"
import V2 from "../../components/V2"
import V3 from "../../components/V3"
import {INCREMENT,DECREMENT} from "../../store/mutation-types"
import { mapMutations } from "vuex"
export default {
    name:"Home",
    data(){
        return{
            v2Msg:"1",
            addNum:10,
            minNum:5
        }
    },
    components:{
        V1,
        V2,
        V3
    },
    methods: {
        v1MsgHandler(data){
            console.log(data);
            this.v2Msg=data;
        },
        ...mapMutations([INCREMENT,DECREMENT]),
        AddHandler(){
            //做增加操作
            // this.$store.commit(INCREMENT,this.addNum)
            this.INCREMENT(this.addNum)

        },
        ReduceHandler(){
            //做增加操作
            this.$store.commit(DECREMENT,8045646)
        },
    },
}
</script>

<style scope>

</style>