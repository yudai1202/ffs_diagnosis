<template>
  <div class="columns is-centered">
    <section class="survey section column is-two-thirds">
      <b-progress type="is-info" v-bind:value="progressVal"></b-progress>
      <p class="question">{{ question.n }}.{{ question.q }}</p>
      <div class="buttons level-item has-text-centered">
        <b-button class="button yes" v-on:click="sendYes">はい</b-button>
        <b-button class="button neither" v-on:click="sendNeither">どちらでもない</b-button>
        <b-button class="button no" v-on:click="sendNo">いいえ</b-button>
        <!-- <div>{{ factors }}</div> -->
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      questions: {
        'a1': '時間の約束には特に厳しい',
        'a2': '小さな不正でもウヤムヤにできない',
        'a3': '理想の実現のため、着実な努力をしている',
        'a4': '他人の言葉をさえぎっても自分の考えを述べる傾向がある',
        'a5': '後輩など目下の者を厳しく教育する',
        'a6': '他人に対して責任感を強く要求する',
        'a7': '他人のミスを厳しく追求、批判することが多い',
        'a8': '権利の主張は、義務を果たした後だと考える',
        'a9': '「こうでなければならない」「こうすべきだ」という表現をよく使う',
        'a10': '規則、道徳、倫理などは、自分の考えより重視する',
        'b1': '他人に対する思いやりは強い',
        'b2': '相手の話に影響を受け、共感しやすい',
        'b3': '何事にも臨機応変に対応できる',
        'b4': '他人の長所を見つけるのは得意',
        'b5': '掃除、洗濯、整理整頓が好き',
        'b6': '子供や他人の世話をするのが好き',
        'b7': '義理や人情といった感情を重視する',
        'b8': 'ボランティアに参加するのが好き',
        'b9': '都合の悪い頼まれ事でも、なかなか「いや」といえない',
        'b10': '目下の者の失敗には寛大である',
        'c1': '感情的な会話は少ない',
        'c2': '将来のことを冷静に予測し、合理的と思う方法で行動している',
        'c3': '調子の悪いときは大事をとって決して無理をしない',
        'c4': '賛否両論をよく聞き自分の意見の参考にしている',
        'c5': '物事の決断はスピーディーである',
        'c6': '行動に際し、自分の損得が優先する',
        'c7': '物事は分析的によく考えてからハッキリ決める',
        'c8': '仕事は能率的に素早く片づけている',
        'c9': '何事も「意見ではなく事実」に基づいて判断している',
        'c10': '情緒的というより論理的である',
        'd1': '欲しいものはすぐに手に入れないと、気がすまない',
        'd2': '感動しやすく涙もろい',
        'd3': '娯楽・飲食などは、満足するまで求める傾向がある',
        'd4': '深く考えるというより、直感で判断することが多い',
        'd5': '燃えやすく、冷めやすい',
        'd6': 'オーバーな表現や、流行語をよく使う',
        'd7': '思った事は、すぐ口に出してしまう',
        'd8': '怒りっぽい',
        'd9': '自分はワガママだと思う',
        'd10': '図に乗るとハメをはずし、度を越すこともある',
        'e1': '争ってまで自分の考えを通すのきらい',
        'e2':'思っていることをなかなか口に出せないことがある',
        'e3':'他人の言葉や行動が気になる',
        'e4':'少数派になるより、多数派でいることのほうが好き',
        'e5':'遠慮がちで消極的な方である',
        'e6':'八方美人的なところが多い',
        'e7':'つらい時は、動くよりじっとガマンしてしまう',
        'e8':'他人の期待に応えるため、過剰な努力をすることがある',
        'e9':'劣等感を強く感じることがある',
        'e10':'人前では、感情をおさえてしまうことが多い',
        's1': '涼しい日でも汗をかくことがある',
        's2': '便秘や下痢をしやすい',
        's3': '目が疲れやすいと感じる',
        's4': '食欲がないと感じることが、時々ある',
        's5': 'スッキリした気分で目覚めることが少ない',
        's6': '肩や首が凝ることがよくある',
        's7': 'カゼをひきやすい',
        's8': '胃や腸には自信がない',
        's9': '頭痛に悩まされることがよくある',
        's10': 'なかなか寝つけないことがある',
        // 'o1': 'よく知らない事を知ったかぶりすることはない',
        // 'o2': '「全体の利益」が「個人的な利益」に優先するのは当然である',
        // 'o3': '下品な冗談を面白いと思ったことはない',
        // 'o4': 'ウソをついたことはない',
        // 'o5': '競争に勝ったときの満足感は何物にも替え難い',
        // 'o6': '周囲の者が競争している姿は微笑ましい',
        // 'o7': '地位や仕事がその人の価値を決める、という意見は理解できる',
        // 'o8': '自慢話はした事がない',
        // 'o9': '他人に言えないような考えが心に浮かんだ事はない',
        // 'o10': '名刺は、個人名より社名が大きいのが自然である',
        // 'o11': '悪口や陰口は決して言わない',
        // 'o12': '自分の能力を思い切り発揮し、自分にしかできないことをしたいと強く思う',
        // 'o13': '知らなかった考え方や物事には強く興味をひかれ、よく知ろうとする',
        // 'o14': '子供の頃、言われた事はすぐ素直にやった',
        // 'o15': '手紙を受け取ったら、いつもすぐ返事をかく',
        // 'o16': '仕事でも個人的な生活場面でも沢山の体験をしたい',
        // 'o17': '自分の考えは、いつも公平である',
        // 'o18': '「何をするか」より「結果の効果」を考えて行動するのが多い',
        // 'o19': '知っている人の中に、嫌いな人はいない',
        // 'o20': 'ほとんどの場合、自分の意見や考え方を強く主張する',
      },
      factors: {
        'a': 0,
        'b': 0,
        'c': 0,
        'd': 0,
        'e': 0,
        's': 0
      },
      timerId: 0,
      intervalId: 0,
      progressVal: 0,
      progressTimerId: 0,
    }
  },
  computed: {
    question () {
      /*
        画面に表示する質問文を選択する機能

        Parameters
        ----------

        Returns
        -------
        k : questionsのkey ex)a1, b1, s1...
          それぞれの因子の質問であることを示すための識別子
        v : questions
          表示する質問の内容
        n : 質問の番号。全80問の内、何番目の質問か
      */
      let keys = Object.keys(this.questions);
      let k = keys[Math.floor(Math.random() * keys.length)];
      let q = this.questions[k];
      let n = 81 - keys.length;
      return {k, q, n}
    }
  },
  methods: {
    recordAnswer (ans) {
      let key = this.question.k;
      let num = this.question.n;
      let factor = key.slice(0, 1);
      this.factors[factor] += ans;
      this.updateQuestions(key, num);
      this.stopTimer()
    },
    updateQuestions(key, num) {
      this.$delete(this.questions, key);
      // 全80問が終わったら、結果ページへ遷移する
      if (num == 80) {
        this.$router.push({
          name: 'result',
          params: {factors: this.factors}
        })
      }
    },
    sendYes() {
      this.recordAnswer(2)
    },
    sendNeither() {
      this.recordAnswer(1)
    },
    sendNo(){
      this.recordAnswer(0)
    },
    startTimer () {
      let timeLimit = 9000 // マイクロ秒
      this.timerId = setTimeout(
        this.sendNeither
        , timeLimit);
    },
    stopTimer () {
      clearTimeout(this.timerId);
    },
    // updateProgress() {
    //   this.intervalId = setInterval(() => {
    //     this.progressVal += 1;
    //     if  (this.progressVal >= 100) {
    //       this.resetProgress()
    //     }
    //   }, 90)
    // },
    // resetProgress() {
    //   clearInterval(this.intervalId);
    //   this.progressVal = 0;
    // }
  },
  watch: {
    question() {
      this.startTimer()
    }
  }
}
</script>

<style scoped>
.question {
  margin-bottom: 40px;
}
</style>
