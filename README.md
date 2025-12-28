<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Minha Rayssa</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Playfair+Display:italic,wght@400;700&display=swap');

        body {
            background-color: #fce4ec;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            font-family: 'Playfair Display', serif;
            overflow-x: hidden;
        }

        .container {
            text-align: center;
            position: relative;
            width: 100%;
            max-width: 600px;
            padding: 20px;
        }

        /* Estilo do Envelope / Coração */
        .heart-icon {
            font-size: 100px;
            color: #d32f2f;
            cursor: pointer;
            filter: drop-shadow(0 5px 15px rgba(0,0,0,0.2));
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        .btn-abrir {
            background-color: #d32f2f;
            color: white;
            border: none;
            padding: 15px 35px;
            font-size: 1.3rem;
            border-radius: 50px;
            cursor: pointer;
            font-family: 'Dancing Script', cursive;
            box-shadow: 0 4px 15px rgba(211, 47, 47, 0.4);
            margin-top: 20px;
            transition: 0.3s;
        }

        /* Carta */
        #carta {
            display: none;
            background: #fffaf0;
            padding: 40px;
            border-radius: 5px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            text-align: left;
            border: 1px solid #eee;
        }

        .texto-carta {
            color: #333;
            line-height: 1.8;
            font-size: 1.1rem;
            white-space: pre-wrap;
        }

        h2 { font-family: 'Dancing Script', cursive; color: #d32f2f; font-size: 2.5rem; margin-top: 0; }
        .assinatura { margin-top: 30px; font-family: 'Dancing Script', cursive; font-size: 1.5rem; text-align: right; color: #d32f2f; }

        /* Esconder o player de vídeo */
        #player { display: none; }

        @media print {
            #interface-inicial, #player { display: none !important; }
            #carta { display: block !important; box-shadow: none; border: none; }
            body { background: white; }
        }
    </style>
</head>
<body>

<div id="player"></div> <div class="container">
    <div id="interface-inicial">
        <div class="heart-icon" onclick="abrirCarta()">❤</div>
        <p>Uma surpresa para você, Rayssa...</p>
        <button class="btn-abrir" onclick="abrirCarta()">Clique para abrir com música</button>
    </div>

    <div id="carta">
        <h2>Para minha eterna Rayssa...</h2>
        <div class="texto-carta">
Eu realmente tenho medo de perder você, porque você é uma pessoa muito especial pra mim, uma pessoa muito importante, eu amo vc, como eu nunca amei ngm, você é o meu primeiro e último amor único, porque eu vou me casar com você, vou envelhecer ao seu lado, vou ter filhos com você, vou ter vc pro resto da minha vida, eu vou me cuidar para que eu possa continuar com você, para que eu possa ser feliz e viver todo o momento bom, poder desfrutar do melhor da vida ao seu lado. 

me desculpa por nao ser um Homem perfeito, me desculpa por ser falho, me desculpa se alguma vez eu errei e decepcionei você, eu nao quero isso, eu quero ser sua melhor escolha, quero que vc seja feliz comigo, eu quero que vc saiba que eu entrei na sua vida pra te amar! 

eu amo amar você Rayssa, vc me traz de volta, você foi a escada do meu poço, a luz do meu túnel, a chave da vida pra poder viver de novo e de novo, eu te agradeço por me trazer de volta, eu te agradeço por ter me colocado em sua vida, eu te agradeço por ter me escolhido nesse mundo de merda que a gente vive, obrigado por ter me dado oportunidade de viver com você, de ser seu namorado.

Eu vou te amar para sempre, cada dia, cada segundo cada minuto, hora dessa vida, por que o meu amor por você, é enorme!!

eu juro que vou te dar muito orgulho, eu juro que vou ser o melhor namorado, o melhor marido, o melhor pai, e o melhor avo do mundo.

quero que saiba que vc pode contar comigo sempre, confiar em mim, ate no seu segredo mais sombrio, mais tenebroso do que possa existir, eu estou com você meu anjo, pra qualquer coisa, pra qualquer situação, e momento.

Eu quero que saiba, que vc nao errou em me escolher, eu quero que saiba que vc é tudo pra mim, que eu te amo, e que sem sombras de dúvidas eu sou todo seu!
        </div>
        <div class="assinatura">Com todo o meu amor para sempre.</div>
    </div>
</div>

<script>
    // 1. Carrega a API do YouTube
    var tag = document.createElement('script');
    tag.src = "https://www.youtube.com/iframe_api";
    var firstScriptTag = document.getElementsByTagName('script')[0];
    firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

    var player;
    function onYouTubeIframeAPIReady() {
        player = new YT.Player('player', {
            height: '0',
            width: '0',
            videoId: 'xua1aWzCRZM', // ID do vídeo do Moby
            playerVars: {
                'start': 15,    // Começa em 0:15
                'end': 143,     // Termina em 2:23 (143 segundos)
                'controls': 0,
                'showinfo': 0,
                'rel': 0
            },
            events: {
                'onStateChange': onPlayerStateChange
            }
        });
    }

    function onPlayerStateChange(event) {
        // Se o vídeo acabar antes de fechar a página, ele para
        if (event.data == YT.PlayerState.ENDED) {
            player.stopVideo();
        }
    }

    function abrirCarta() {
        // Mostra a carta e esconde o botão
        document.getElementById('interface-inicial').style.display = 'none';
        document.getElementById('carta').style.display = 'block';
        
        // Toca a música
        if (player && player.playVideo) {
            player.playVideo();
        }
    }
</script>

</body>
</html>
