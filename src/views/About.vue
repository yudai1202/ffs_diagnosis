<template>
  <div class="about columns is-centered">
    <div class="card column is-two-thirds">
      <h1>FFS診断前に確認していただきたいこと</h1>
      <div>
        <section class="caution">
          <h2>診断の際の注意事項</h2>
          <ul>
            <li>「スタート」ボタンをクリックすると、質問文の表示が開始されますので、「はい」「どちらでもない」「いいえ」のボタンをクリックして回答します。</li>
            <li>質問は全部で80問あります。かんたんな内容ですので、あまり考え込まず、直感で回答してください</li>
            <li>受検は1回のみ、可能です。</li>
            <li>9秒を経過すると自動的に「どちらでもない」を選択肢次の質問に進みます。</li>
            <li>位置停止はできません。万一、明らかに"間違った"と思う回答をした場合は、一旦回答を中止し、ブラウザを閉じ、最初からやり直してください。</li>
            <li>そのまま放置すると、以降の質問を全て「どちらでもない」として、終了してしまいますのでご注意ください。</li>
            <li>回答完了後は、「スタート」ボタンは表示されなくなり、再受検できなくなります。</li>
          </ul>
        </section>
        <section class="attitude">
          <h2>受検の際の心構え</h2>
          <ul>
            <li>診断においては、あまり考え込まず、直感で回答してください。</li>
            <li>質問の中で信頼度(回答の精度)も図っていますので、「理想像」としての回答などは、信頼度に現れます。できるだけ「素」の回答を心がけて下さい。</li>
          </ul>
        </section>
      </div>
      <router-link to="/survey" class="button is-info" type="is-primary" size="is-large">スタート</router-link>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
h2 {
  text-align: left;
}

section {
  padding: 0px 40px;
  margin-bottom: 30px;
}

ul {
  text-align: left;
}

li {
  list-style-type: disc;
}
</style>