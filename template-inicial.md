# 🧭 CVE-Hunters — Guia de Onboarding

Bem-vindo(a) ao **CVE-Hunters**!  
Aqui você aprende na prática a caçar vulnerabilidades, reportar CVEs e contribuir com a segurança de softwares de impacto social e global.  
Atualmente estamos nos reunindo no Discord para tirar dúvidas e colaborar: https://discord.gg/3GJvV6xPeg

---

## 🚀 Primeiros Passos 
Entre no nosso Discord: https://discord.gg/3GJvV6xPeg
1. Você recebe a role **`CVE-Hunter`**.  
2. Ganha acesso aos canais:
   - `#projetos`
   - `#dicas`
   - `#recursos`
   - `#reports-rápidos`
3. Leia o post fixado **“Como trabalhamos”** e a política de **divulgação responsável**.  
4. Lembre-se: aqui você aprende fazendo — não damos a solução de mão, mas ajudamos no caminho.  

---

## 🔄 Fluxo do Novato

### 1) Escolha um projeto:
- Veja o canal `#projetos-ativos` e comece a colaborar com um dos projetos que temos ativos.


### 2) Encontrou algo? Faça a **auto-triagem inicial**
Responda:
- É reproduzível? (sim/não)  
- Requer credenciais? (sim/não)  
- Pode causar impacto em produção? (sim/não)  
- Tipo provável (BOLA, XSS, SQLi, RCE, etc.)  
- Probabilidade de falso-positivo (alta/média/baixa)  

### 3) Peça revisão a um **Senior**
- Crie um **thread** no canal `#💬╺╸chat-geral-acesso` e marque @📕╺╸CVE-Hunter Sênior para ajudar na validação.
- Título: `[Found] <sistema> — possível <tipo> (preliminar)`  
- Suba sua POC em um local privado e compartilhe o link diretamente com o @📕╺╸CVE-Hunter Sênior que for te ajudar.
- Não suba POC em locais públicos.
- O Senior revisa, valida o risco e orienta o próximo passo.  

### 4) Trabalhe no **report interno**
- Junto com o Senior, monte um relatório com:
  - Resumo executivo  
  - Steps to Reproduce  
  - Impacto  
  - Evidências sanitizadas  
  - Mitigação sugerida  
  - CVSS provisório

### 5) Disclosure
- Senior e Novato decidem fluxo: vendor, CNA, ou publicação direta.  
- Sempre seguir política de **responsible disclosure**.
- Marque o CVE-Hunters no report sempre que possível.

### 6) Publicação
- Após fix ou fim do embargo → publicar advisory oficial.
- Faça PR no Git do CVE-Hunters para publicação em nosso site. 
- O Novato é promovido a **`Aspirante`** 🎉  

---

## ⭐ Regras de Ouro
- **Nunca** postar PoC público antes do disclosure autorizado.  
- **Sempre** pedir revisão de um Senior antes de contato externo.  
- **Documentar tudo** no tracker do grupo.  
- **Aprender fazendo** — os Seniors guiam, não executam por você.  

---

## 🎯 Critérios para virar `Aspirante`
Você se torna **Aspirante** quando:
- Completar o ciclo completo (descoberta → publicação) em pelo menos 1 CVE **ou**  
- Ajudar tecnicamente em 2 achados aprovados por Senior **ou**  
- Demonstrar conhecimento das políticas internas e conduzir disclosure com mínima supervisão.  

**Benefícios de Aspirante**:  
- Acesso a categorial ──── 🏹 ✦ CVE-HUNTERS PRINCIPAL.  
- Participar de calls de triagem.
- Hall da Fama
- Posts no Linkedin
- Reports privados
- Payloads Privados

---

## 📝 Templates

LINK PARA TEMPLATES: 




🧭 Agora é com você!
Dê o primeiro passo, poste seu achado em #reports-rápidos e comece sua jornada como CVE-Hunter.
