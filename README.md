<img width="1000" height="220" alt="banner" src="https://github.com/user-attachments/assets/07857c15-5348-418a-b03c-c73d8c1b91bc" />
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 220" width="1000" height="220" xmlns:c2pa="http://c2pa.org/manifest"><metadata><c2pa:manifest></metadata>
<defs>
  <linearGradient id="bg" x1="0" y1="0" x2="1" y2="1">
    <stop offset="0" stop-color="#000000"/>
    <stop offset="0.65" stop-color="#05060d"/>
    <stop offset="1" stop-color="#12002b"/>
  </linearGradient>
  <linearGradient id="scan" x1="0" y1="0" x2="0" y2="1">
    <stop offset="0" stop-color="#00FF9C" stop-opacity="0"/>
    <stop offset="0.5" stop-color="#00FF9C" stop-opacity="0.16"/>
    <stop offset="1" stop-color="#00FF9C" stop-opacity="0"/>
  </linearGradient>
  <linearGradient id="beam" x1="0" y1="0" x2="1" y2="0">
    <stop offset="0" stop-color="#00FF9C" stop-opacity="0"/>
    <stop offset="0.5" stop-color="#00FF9C" stop-opacity="1"/>
    <stop offset="1" stop-color="#00FF9C" stop-opacity="0"/>
  </linearGradient>
  <filter id="glow" x="-20%" y="-50%" width="140%" height="200%">
    <feGaussianBlur stdDeviation="4" result="b"/>
    <feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge>
  </filter>
  <clipPath id="frame"><rect width="1000" height="220" rx="10"/></clipPath>
</defs>
  <rect width="1000" height="70" fill="url(#scan)">
    <animateTransform attributeName="transform" type="translate" from="0 -70" to="0 220" dur="3.5s" repeatCount="indefinite"/>
  </rect>
  <rect y="217" width="1000" height="3" fill="#00FF9C" fill-opacity="0.25"/>
  <rect y="217" width="260" height="3" fill="url(#beam)">
    <animate attributeName="x" from="-260" to="1000" dur="2.8s" repeatCount="indefinite"/>
  </rect>
</g>
<rect x="0.5" y="0.5" width="999" height="219" rx="10" fill="none" stroke="#00FF9C" stroke-opacity="0.35"/>
</svg>

<p align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=16&duration=2200&pause=800&color=00FF9C&background=00000000&multiline=true&width=700&height=190&lines=%24+whoami;3m3r4l;%24+forge+test+--match-test+testExploit+-vvvv;%5B%2B%5D+flash+loan+borrowed%3A+1%2C000%2C000+tokens;%5B%2B%5D+oracle+price+manipulated;%5BPASS%5D+testExploit%28%29+%28gas%3A+1337%29+%E2%9C%94;%2F%2F+responsible+disclosure+only+%F0%9F%8E%A9" alt="Typing SVG" />
  </a>
</p>

```bash
$ whoami
3m3r4l

$ cat /etc/identity
role     : smart contract hacker (white hat) 🎩
chains   : Sui · Solana(devnet) · EVM
weapons  : Move · Rust · Solidity · JavaScript
target   : cualquier contrato que diga "es seguro, confía"
motto    : "My only crime is curiosity"
```

---

### 🧬 `module whitehat::profile`

```move
module whitehat::profile {

    struct Hacker has key, store {
        handle: String,          // "3m3r4l"
        bio: String,             // "My only crime is curiosity"
        langs: vector<String>,   // ["Move", "Rust", "JavaScript"]
        curiosity: u64,          // u64::MAX
        bugs_found: u64,         // en construcción 🚧
    }

    public fun hunt(h: &mut Hacker, target: &Contract) {
        assert!(target.has_bug(), E_NOT_YET);   // siempre hay un bug...
        h.bugs_found = h.bugs_found + 1;        // ...solo hay que encontrarlo
    }
}
```

---

### 💀 `bug_of_the_day.sol`

```solidity
// ⚠️ Spot the bug. Reentrancy clásico.
contract Vault {
    mapping(address => uint) public balances;

    function withdraw() external {
        uint amount = balances[msg.sender];
        (bool ok, ) = msg.sender.call{value: amount}("");   // 💥 interacción antes del efecto
        require(ok);
        balances[msg.sender] = 0;                           // 🐛 demasiado tarde
    }
}
// fix: Checks → Effects → Interactions (o nonReentrant)
```

---

### 🎯 `attack_surface.md`

| Vector | Qué busco | Estado |
|:--|:--|:--:|
| 🔁 Reentrancy | Llamadas externas antes de actualizar estado | 🔎 estudiando |
| ⚡ Flash loans / flash swaps | Manipular precios o liquidez en una sola tx | 🛠️ [PoC activo](https://github.com/3m3r4l/Auditory-turbos-flash-swap-PoC) |
| 🔮 Oracle manipulation | Precios fáciles de mover | 🔎 estudiando |
| 🔑 Access control | Funciones sensibles sin permisos | 🔎 estudiando |
| 🧮 Lógica / redondeo | Errores matemáticos y de precisión | 🔎 estudiando |
| 🥪 MEV / front-running | Ordenar transacciones a mi favor | 🔎 estudiando |

---

### 🔬 `methodology.sh`

```bash
[1] RECON      →  leer el código, docs y arquitectura del protocolo
[2] STATIC     →  Slither · Move Prover · revisión manual línea por línea
[3] FUZZ       →  Echidna · Foundry invariants · casos extremos
[4] EXPLOIT    →  escribir el PoC (si no se puede reproducir, no existe)
[5] REPORT     →  severidad · impacto · fix recomendado
[6] REPEAT     →  siguiente contrato 🔁
```

---

### 🧰 `arsenal/`

<p align="center">
  <img src="https://img.shields.io/badge/Move-4DA2FF?style=for-the-badge&logo=sui&logoColor=white" alt="Move" />
  <img src="https://img.shields.io/badge/Rust-1a1a1a?style=for-the-badge&logo=rust&logoColor=white" alt="Rust" />
  <img src="https://img.shields.io/badge/Solidity-363636?style=for-the-badge&logo=solidity&logoColor=white" alt="Solidity" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Foundry-000000?style=for-the-badge&logoColor=00FF9C&labelColor=000000&color=00FF9C" alt="Foundry" />
  <img src="https://img.shields.io/badge/Slither-000000?style=for-the-badge&labelColor=000000&color=ff0055" alt="Slither" />
  <img src="https://img.shields.io/badge/Echidna-000000?style=for-the-badge&labelColor=000000&color=ffaa00" alt="Echidna" />
  <img src="https://img.shields.io/badge/Linux-000000?style=for-the-badge&logo=linux&logoColor=00FF9C" alt="Linux" />
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
</p>

---

### 📂 `$ ls ~/exploits`

| 🔓 Repo | 🧬 Lenguaje | ⚔️ Objetivo |
|:--|:--:|:--|
| [Research-flash-swap-PoC](https://github.com/3m3r4l/Research-flash-swap-PoC) | Move | Auditar y demostrar riesgos en flash swaps |
| [Practicas_Devnet](https://github.com/3m3r4l/Practicas_Devnet) | Rust | Laboratorio de contratos en devnet |
| [dApp-practices](https://github.com/3m3r4l/dApp-practices) | JavaScript | Conectar contratos con interfaces reales |

---

### 📋 `audit_checklist.md`

- [x] Entender la lógica antes de buscar bugs
- [x] Escribir PoCs en lugar de solo teorizar
- [ ] Primer hallazgo reportado en bug bounty 🏴‍☠️
- [ ] Participar en un contest de auditoría (Code4rena / Sherlock / Cyfrin)
- [ ] Publicar un write-up técnico
- [ ] Rankear en un CTF de smart contracts

---

### 📡 `./stats.sh`

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=3m3r4l&show_icons=true&hide_border=true&bg_color=0d1117&title_color=00FF9C&icon_color=00FF9C&text_color=c9d1d9" alt="stats" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=3m3r4l&layout=compact&hide_border=true&bg_color=0d1117&title_color=00FF9C&text_color=c9d1d9" alt="langs" />
</p>

---

```solidity
// gracias por visitar mi contrato 👾
function exit() external {
    emit Visitor(msg.sender, "thanks for stopping by");
    selfdestruct(payable(msg.sender));   // 💨
}
```

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00FF9C,50:1a0033,100:000000&height=100&section=footer" width="100%" alt="footer" />
