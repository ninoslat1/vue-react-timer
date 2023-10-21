<script>
export default {
 props: ['score'],
 data () {
    return {
        rank: null,
    }
 },
 mounted() {
    if(this.score < 250) {
        this.info(this.score, this.rank = "Ninja Fingers")
    } else if (this.score > 250 && this.score < 400){
        this.info(this.score, this.rank = "Rapid Reflexes")
    }
    else {
        this.info(this.score, this.rank = "Snail Pace...")
    }
 },
 methods: {
    info(rank, score){
        return alert(`Hey you got ${this.score} ms reaction time. Your rank is ${this.rank}`)
    }
 }
}
</script>