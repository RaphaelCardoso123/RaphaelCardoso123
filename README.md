## Olá pessoal, sejam bem vindos ao meu GitHub 👋

 Meu nome é Raphael Cardoso, sou programador Trainee na empresa Benner e aqui é onde pratico meus estudos, aprendizado e publico alguns projetos.

<!--
**RaphaelCardoso123/RaphaelCardoso123** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

languages = {}
total_lines = 0

for repo in repositories:
    repo_url = repo["languages_url"]
    repo_response = requests.get(repo_url, headers=headers)
    repo_languages = repo_response.json()

    for language, lines in repo_languages.items():
        if language in languages:
            languages[language] += lines
        else:
            languages[language] = lines

        total_lines += lines
average = total_lines / len(languages)
for language, lines in languages.items():
    print(f"{language}: {lines / total_lines * 100:.2f}%")

print(f"Average lines per language: {average}")
