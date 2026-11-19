---
name: qg
description: Quartier général. Passe une demande au QG, qui choisit parmi tous les skills et agents de l'utilisateur ceux qui conviennent, puis exécute l'ordre de mission. Activer sur "/qg <demande>", "qg", "quartier général", "quel skill utiliser", "quel agent utiliser", "qui doit s'en occuper". NOT pour une demande qui nomme déjà le skill ou l'agent à utiliser.
---

# /qg — passer par le quartier général

Utilise ce skill quand l'utilisateur tape `/qg <demande>` ou demande quels skills ou agents utiliser.

## Étapes

1. **Demander l'ordre de mission.** Lance l'agent `quartier-general` avec :
   - la demande de l'utilisateur, mot pour mot ;
   - la liste des skills et des types d'agents disponibles dans cette session (copie leurs noms), pour qu'il préfère ce qui est déjà installé.

   Si l'agent `quartier-general` n'est pas disponible, fais son travail toi-même : lis `.claude/agents/quartier-general/AGENT.md` dans le dépôt `some_claude_skills` et suis-le.

2. **Montrer l'ordre de mission** à l'utilisateur en quelques lignes : skills retenus, agents retenus, déroulé.

3. **Exécuter.**
   - Charge chaque skill retenu avec l'outil Skill.
   - Lance les agents retenus avec l'outil Agent, en parallèle quand l'ordre de mission le dit, en leur donnant la sous-tâche exacte et les conventions des skills chargés.
   - Si un élément est « à installer », ne l'installe pas sans accord : propose la commande et continue avec ce qui est disponible.

4. **Rendre compte** : ce qui a été fait, par qui, et ce qui reste (les « Manques » de l'ordre de mission).

Si l'utilisateur veut seulement savoir quoi utiliser (« quel skill… ? »), arrête-toi après l'étape 2.
