<script setup>
import logo from "../assets/logo.png";
import nacim from "../assets/nacim.png";
import adelia from "../assets/adelia.png";
import david from "../assets/david.png";
import linkedinimg from "../assets/linkedin.png";
import github from "../assets/github.png";
import youtube from "../assets/youtube.png";
import MVP from "../assets/MVP.mp4";
import nathan from "../assets/nathan.png";
import jules from "../assets/jules.png";
import { ref } from "vue";

const team = [
  {
    id: 1,
    name: "LAFON Nathan",
    role: "Bachelor 3 - Infra & SI",
    description: "J'ai participé au déploiement du site web et à sa sécurisation.",
    image: nathan,
    link: "https://www.youtube.com/watch?v=dQw4w9WgXcQ",
    imglink: youtube,
    linkname: "Youtube",
  },
  {
    id: 2,
    name: "SEREIR Nacim",
    role: "Bachelor 3 - Développement",
    description:
      "J'ai participé à la réalisation du site vitrine, à la partie front-end du projet et au développement du jeu.",
    image: nacim,
    link: "https://www.linkedin.com/in/nacim-sereir",
    imglink: linkedinimg,
    linkname: "LinkedIn",
  },
  {
    id: 3,
    name: "NGUYEN David",
    role: "Bachelor 3 - Data",
    description: "J'ai participé à la mise en place des websockets et au développement du jeu.",
    image: david,
    link: "https://www.linkedin.com/in/david-nguyen-4412a322b/",
    imglink: linkedinimg,
    linkname: "LinkedIn",
  },
  {
    id: 4,
    name: "BESSON Jules",
    role: "Bachelor 2",
    description: "J'ai participé à la réalisation de la partie back-end du projet.",
    image: jules,
    link: "https://github.com/CactusNormal7",
    imglink: github,
    linkname: "GitHub",
  },
  {
    id: 5,
    name: "FATHIPOURSASANSARA Sajedeh Adelia",
    role: "B3 Informatique - Développement",
    description: "J'ai participé à la partie front-end du projet.",
    image: adelia,
    link: "https://github.com/SajedehAdelia",
    imglink: github,
    linkname: "GitHub",
  },
];

function playMusic() {
  const musicPlayer = document.getElementById("music-player");
  musicPlayer.play();
}

const toggleMemberLinkedIn = (member) => {
  if (selectedMember.value && selectedMember.value.id === member.id) {
    member.isSelected = false;
    member.isHovered = false;
    selectedMember.value = null;
  } else {
    member.isSelected = true;
    member.isHovered = true;
    selectedMember.value = member;
  }
};

const selectedMember = ref(null);
</script>

<template>
  <div>
    <div class="main-title">présentation du projet</div>
    <div class="container-presentation">
      <div class="logo-container">
        <img src="../assets/logo.png" class="logo" @click="playMusic" />
        <audio id="music-player" controls style="display: none">
          <source src="../assets/drums.mp3" type="audio/mpeg" />
        </audio>
      </div>
      <div class="text-container">
        <div class="presentation">
          QuizTune est une plateforme web qui prend la forme d’un jeu de quiz musical. Les
          utilisateurs s'affrontent en temps réel, reconnaissant des morceaux audio ou des
          extraits sous forme de texte de tous genres et époques. Grâce à une interface
          intuitive, les joueurs peuvent se défier entre amis et créer leurs propres
          parties. Avec QuizTune, vivez la musique sous un angle ludique et compétitif.
          Rejoignez la mélodie, testez vos connaissances !
        </div>
      </div>
    </div>

    <div class="horizontal-line">
      <div class="line"></div>
    </div>

    <div class="container-team">
      <div class="team-title">présentation de l'équipe</div>
      <div class="team-cards">
        <div
          class="team-card"
          v-for="member in team"
          @click="toggleMemberLinkedIn(member)"
          @mouseover="member.isHovered = true"
          @mouseleave="member.isHovered = false"
          :class="{ 'team-card-hovered': member.isHovered }"
        >
          <img class="member-image" :src="member.image" />
          <div class="member-name">{{ member.name }}</div>
          <div class="member-role">{{ member.role }}</div>
          <div class="member-description">{{ member.description }}</div>
          <div
            v-if="selectedMember && selectedMember.id === member.id"
            class="member-linkedin"
          >
            <img :src="member.imglink" class="linkedin" />
            <a :href="member.link" target="_blank"
              >{{ member.name }} sur {{ member.linkname }}</a
            >
          </div>
        </div>
      </div>
    </div>

    <div class="horizontal-line">
      <div class="line"></div>
    </div>

    <div class="container-functionnalities">
      <div class="functionnalities-title">Fonctionnalités</div>
      <div class="container-listfunctionnalities">
        <div class="functionnalities">
          <div class="functionnalities-name">Fonctionnalités MVP</div>
          <div class="functionnality">
            • Pas de système de compte, seulement un pseudo
          </div>
          <div class="functionnality" style="flex-direction: column">
            • Différents types de questions :
            <p>- choix multiples, vraie/fausse, compléter la phrase etc...</p>
            <p>
              - Lancer un extrait et poser des questions dessus (nom de l’artiste/du
              groupe, titre de la chanson, année de sortie, paroles…)
            </p>
          </div>
          <div class="functionnality">
            • Attribuer des points en fonction de la rapidité et de l’exactitude des
            réponses
          </div>
          <div class="functionnality">
            • Websocket pour jouer en temps réel entre les joueurs
          </div>
        </div>
        <div class="functionnalities">
          <div class="functionnalities-name">Fonctionnalités v2 site web</div>
          <div class="functionnality">
            • Permettre à un utilisateur de créer une salle privée avec un code d’accès
          </div>
          <div class="functionnality">
            • Permettre à un utilisateur de rejoindre la partie créée avec le code d’accès
          </div>
          <div class="functionnality">
            • Différents modes de jeu : full mp3, full vrai/faux, full qcm, mixte.
          </div>
          <div class="functionnality">• Chronomètre pour répondre à chaque question</div>
          <div class="functionnality">• Afficher les scores en temps réel</div>
          <div class="functionnality">• Système de chat</div>
          <div class="functionnality">
            • Paramétrer la partie (mode, durée des questions, clôture des questions)
          </div>
          <div class="functionnality">• Nombre de points maximum par partie</div>
          <div class="functionnality">• Classement final</div>
          <div class="functionnality">• Déploiement du site web</div>
          <div class="functionnality">• Sécurisation du site web</div>
        </div>
      </div>
    </div>
    <div class="horizontal-line">
      <div class="line"></div>
    </div>

    <div class="container-video">
      <div class="video-title">Vidéo de présentation du MVP</div>
      <video controls class="video">
        <source src="../assets/MVP.mp4" type="video/mp4" />
      </video>
    </div>

    <div class="horizontal-line">
      <div class="line"></div>
    </div>

    <div class="container-repository">
      <div class="repository-title">Liens de notre projet</div>
      <div class="repository">
        <a
          class="repository-name"
          href="https://github.com/CactusNormal7/hackathon_final.git"
        >
          Dépôt GitHub
        </a>
        <a
          class="repository-name"
          href="https://trello.com/invite/b/iJMO4yNx/ATTI6fb1ec4e3de645e8bc302b9fdfd0af96745FC3F9/hackathon"
        >
          Trello
        </a>
      </div>
    </div>
  </div>
</template>
