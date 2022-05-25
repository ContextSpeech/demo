---
layout: default
---

# Abstract
Although Text-to-Speech (TTS) has made rapid progress in speech quality at sentence level, it still faces a lot of challenges in paragraph / long-form reading. Synthesizing sentence by sentence in a paragraph and then concatenating them together will cause inconsistent issues that affect paragraph-level expressiveness. While directly modelling all the sentences in a paragraph will incur large computation / memory cost. In this paper, we develop a TTS system called ContextSpeech, which models the contextual information in a paragraph for coherence and expressiveness without largely increasing the computation or memory cost. On the one hand, we introduce a memory-cached recurrence mechanism to let the current sentence see more history information both on the text and speech sides. On the other hand, we construct text-based semantic information in a hierarchical structure, which can broaden the horizon and incorporate the future information. Additionally, we use a linearized self-attention with compatible relative-position encoding to reduce the computation / memory cost. Experiments show that ContextSpeech significantly improves the paragraph-level voice quality and prosody expressiveness in terms of both subjective and objective evaluation metrics. Furthermore, ContextSpeech achieves better model efficiency in both training and inference stage.

# Contents
- [Abstract](#abstract)
- [Audio Samples](#audio-samples)
  * [Recordings](#recordings)
  * [Paragraphs with normal sentence](#paragraphs-with-normal-sentence)
  * [Paragraphs with extra-short sentence](#paragraphs-with-extra-short-sentence)
  * [Paragraphs with extra-long sentence](#paragraphs-with-extra-long-sentence)

# Audio Samples

## Recordings
<table align="center">
    <tr><th>Transcript</th><th>Recording</th></tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
            这世界上有千百种各式各样的死法儿,可你知道最恐怖的死法儿是哪一种吗?我知道……因为此时此刻,我就亲眼见识到了。咕噜噜……一个黑影儿滚到了我的脚下,虽然此刻周围的灯光昏暗阴森,我却依然能清楚的看到那是什么。那是我的同事姜开的脑袋……
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Recording/indomain.wav"></audio><br>
        </td>
    </tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
            看着姜开张大着嘴,死不瞑目的面容,我先是觉得脖子后面儿凉风嗖嗖直冒,脑门上也见了汗,紧接着,一阵反胃恶心的感觉便从胃里直冲嗓子眼。然而这个时候儿,那种感觉却一下子堵在了脖子里,我想要挪动一下步子,身体也根本无法动弹。
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Recording/indomain.wav"></audio><br>
        </td>
    </tr>  
</table>

## Paragraphs with normal sentence

<table align="center">
    <tr><th>Transcript</th><th>Baseline</th><th>ContextSpeech</th></tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
            看着姜开张大着嘴,死不瞑目的面容,我先是觉得脖子后面儿凉风嗖嗖直冒,脑门上也见了汗,紧接着,一阵反胃恶心的感觉便从胃里直冲嗓子眼。然而这个时候儿,那种感觉却一下子堵在了脖子里,我想要挪动一下步子,身体也根本无法动弹。
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Baseline/indomain.wav"></audio><br>
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/ContextSpeech/indomain.wav"></audio><br>
        </td>
    </tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
            不管怎么样,她都在我完全没有准备的时候出现在了我的身边,手里拿着一个匕首就朝着我刺了过来,我根本没时间躲。下意识的,我抬起手就朝着红衣女人一拳打了过去。不过当我的拳头在半空飞行的时候儿,我却忽然想起一件事,那就是我身边的这个红衣女人,在力量上可是几乎可以与林千怡媲美的存在啊,和她们的力量比起来。我这一拳岂不是如同棉花一样软绵绵的一拳呐,不但不可能伤到对方,反而恐怕要激起对手的愤怒,而现在病房角落里,躺着的两个混混儿的尸体,恐怕就是我几秒钟之后的下场了。
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Baseline/indomain-2.wav"></audio><br>
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/ContextSpeech/indomain-2.wav"></audio><br>
        </td>
    </tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
            车厢门口空荡荡的。只剩下原本要跳车的沈援朝几人，凭他们要拦住怪物看似不可能。怪物直冲过去，眼看就要跳离车厢，白发男暗叫一声大意了，跳起来一蹬车厢壁，借着这一蹬之力越过了满地的黑血，伸出短剑直奔怪物的后心，只可惜还是晚了一拍，怪物的双脚已经离地，眼瞅就能逃出车厢。
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Baseline/1-1.wav"></audio><br>
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/ContextSpeech/1-1.wav"></audio><br>
        </td>
    </tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
            “当”的一声响，铁铲砍破了麻袋，响起了一阵金属相击才能产生的共鸣，一串火花闪过，铁铲被弹起老高。这一铲似乎起到了效果，麻袋的抖动停止了。还没等众人高兴起来，就听得“嘭”的一声，绑在麻袋上的四条牛皮武装带全部被崩开，麻袋也被撕得粉碎。
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Baseline/1-2.wav"></audio><br>
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/ContextSpeech/1-2.wav"></audio><br>
        </td>
    </tr>    
</table>

## Paragraphs with extra-short sentence

<table align="center">
    <tr><th>Transcript</th><th>Baseline</th><th>ContextSpeech</th></tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
          踩着钢钉爬了十来米就看见了宋春雷说的山洞。
          <font color="#FF0000">嘿！</font>
          入口就是个一人多高的缝隙。
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Baseline/short-1.wav"></audio><br>
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/ContextSpeech/short-1.wav"></audio><br>
        </td>
    </tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
          莫特也反应过来，调转枪口打向胖子射击的位置。
          <font color="#FF0000">哟呵！</font>
          枪声停止时，胖子大喝一声，双手捂头后退几步，对着被子弹打过的墙壁猛撞过去。
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Baseline/short-2.wav"></audio><br>
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/ContextSpeech/short-2.wav"></audio><br>
        </td>
    </tr>  
</table>

## Paragraphs with extra-long sentence

<table align="center">
    <tr><th>Transcript</th><th>Baseline</th><th>ContextSpeech</th></tr>
    <tr>
        <td width="60%" style="word-wrap:break-word;">
          在河谷边歇息的片刻，一行数十骑，再度动身，落下一地的烟尘，这个年轻的军官，名叫元徽，是幽州居庸关镇将，正六品的职位，他年纪却不过二十，策马奔腾间，元徽英俊的面上仍旧是一副从容像，但那双鹰一般眼睛中却流露出一丝迷离之意，他是个穿越者，到如今，穿越到这个世界，有近十年了，而这个世界，他早早地便知晓了，这是电视剧《神探狄仁杰》的世界，因为他有个极为厉害的父亲，元齐，当今天子女皇武亲封的颍王，江淮杀手组织铁手团的首领，元齐、铁手团、扬州……这些熟悉的人与事物，曾经带给了他极大的冲击，当年方魂降大唐之时，正处徐敬业造反时期，元徽是眼看着元齐积极逢迎当时临朝称制的太后武氏，凭着铁手团在江淮经营百年的势力，极为主动地配合朝廷平叛，立下大功，徐敬业覆灭之后，朝廷论功行赏，武氏竟然封元齐为颍王，而元徽自然而然地成为了颍王世子，元齐得以成为扬州最有权势的勋略，而因徐敬业之乱，江淮势力受波及，各方都损失惨重。
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/Baseline/long.wav"></audio><br>
        </td>
        <td>
            <audio controls style="width: 150px;"><source src="Samples/ContextSpeech/long.wav"></audio><br>
        </td>
    </tr>
</table>
