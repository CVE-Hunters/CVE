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

### 6) Publicação
- Após fix ou fim do embargo → publicar advisory oficial.  
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
- Acesso ao canal `#coordination`.  
- Pode abrir issues no tracker público.  
- Participar de calls de triagem.  

---

## 📝 Templates

### Pedido de Revisão

TÍTULO: [REVIEW REQUEST] <produto/sistema> — possível <tipo> (preliminar)

Resumo: <1-2 linhas>
Ambiente: <dev/staging/prod>
Evidências: 
- <print>
- <curl -i '...'>

Mini-triagem:
- Reproduzível: (sim/não)
- Requer credenciais: (sim/não)
- Risco percebido: (baixo/médio/alto)
- Pode impactar produção: (sim/não)

O que preciso:
- Revisão do risco
- Orientação sobre PoC seguro
- Próximos passos (vendor/CNA)


Checklist antes de contato com vendor
	•	Steps to reproduce claros
	•	Evidências sanitizadas
	•	CVSS estimado + justificativa
	•	Contato de disclosure mapeado
	•	Timeline registrada
	•	Revisão aprovada por 1 Senior

Template de Relatório Final

# CVE-Hunters Advisory — <produto> — <vulnerabilidade>

## Resumo Executivo
<descrição em 2-3 frases>

## Affected Versions
<lista de versões afetadas>

## Impact
<impacto em confidencialidade, integridade, disponibilidade>

## Technical Details
<steps to reproduce>

## Mitigation
<sugestão de correção ou workaround>

## Timeline
- Descoberta: DD/MM/YYYY
- Contato: DD/MM/YYYY
- Resposta vendor: DD/MM/YYYY
- Fix: DD/MM/YYYY
- Publicação: DD/MM/YYYY

## Credits
<descobridor + CVE-Hunters>

## CVE ID
<quando disponível>

Template de Relatório Final


🧭 Agora é com você!
Dê o primeiro passo, poste seu achado em #reports-rápidos e comece sua jornada como CVE-Hunter.
