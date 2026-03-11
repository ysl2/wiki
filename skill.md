# skill

## Skill source

- <https://skills.sh>
- <https://skillhub.tencent.com/>
- <https://clawhub.ai/>

## Add skills

### Add skills from `http://skills.sh`

```bash
# npx skills add vercel-labs/skills -s find-skills -g -y
# npx skills add vercel-labs/agent-browser -s agent-browser -g -y
npx skills add obra/superpowers -g -y
npx skills add othmanadi/planning-with-files -s planning-with-files -g -y
```

### Add skills from marketplace

```bash
# Ref: https://github.com/anthropics/skills
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills

# Ref: https://github.com/obra/superpowers
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace

# Ref: https://github.com/OthmanAdi/planning-with-files
/plugin marketplace add OthmanAdi/planning-with-files
/plugin install planning-with-files@planning-with-files
```

### Add skills from source

```bash
mkdir -p ~/.claude/skills
cd ~/.claude
git clone git@github.com:anthropics/skills.git skills-anthropics
cd skills
ln -s ../skills-anthropics/skills/* ./
```
