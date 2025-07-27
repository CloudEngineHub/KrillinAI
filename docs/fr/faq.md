### 1. Impossible de voir le fichier de configuration `app.log`, impossible de connaître le contenu de l'erreur
Les utilisateurs de Windows doivent placer le répertoire de travail de ce logiciel dans un dossier qui n'est pas sur le disque C.

### 2. La version non desktop a bien créé le fichier de configuration, mais renvoie toujours l'erreur "Fichier de configuration introuvable"
Assurez-vous que le nom du fichier de configuration est `config.toml`, et non `config.toml.txt` ou autre.
Une fois la configuration terminée, la structure du dossier de travail de ce logiciel devrait être la suivante :
```
/── config/
│   └── config.toml
├── cookies.txt （<- fichier cookies.txt optionnel）
└── krillinai.exe
```

### 3. J'ai rempli la configuration du grand modèle, mais j'obtiens l'erreur "xxxxx nécessite la configuration de la clé API xxxxx"
Bien que les services de modèle et de voix puissent tous deux utiliser les services d'OpenAI, il existe également des scénarios où le grand modèle utilise des services non-OpenAI, c'est pourquoi ces deux configurations sont séparées. En plus de la configuration du grand modèle, veuillez chercher la configuration de whisper en bas pour remplir les clés et autres informations correspondantes.

### 4. L'erreur contient "yt-dlp error"
Le problème du téléchargeur vidéo semble être soit un problème de réseau, soit un problème de version du téléchargeur. Vérifiez si le proxy réseau est activé et configuré dans les options de configuration du fichier, et il est conseillé de choisir un nœud à Hong Kong. Le téléchargeur est installé automatiquement par ce logiciel, la source d'installation sera mise à jour, mais ce n'est pas une source officielle, donc il peut y avoir des retards. En cas de problème, essayez de mettre à jour manuellement, la méthode de mise à jour est :

Ouvrez un terminal dans le répertoire bin du logiciel et exécutez
```
./yt-dlp.exe -U
```
Remplacez `yt-dlp.exe` par le nom réel du logiciel ytdlp sur votre système.

### 5. Après le déploiement, la génération de sous-titres fonctionne normalement, mais les sous-titres intégrés dans la vidéo contiennent beaucoup de caractères illisibles
La plupart du temps, cela est dû à l'absence de polices chinoises sur Linux. Veuillez télécharger les polices [Microsoft YaHei](https://modelscope.cn/models/Maranello/KrillinAI_dependency_cn/resolve/master/%E5%AD%97%E4%BD%93/msyh.ttc) et [Microsoft YaHei Bold](https://modelscope.cn/models/Maranello/KrillinAI_dependency_cn/resolve/master/%E5%AD%97%E4%BD%93/msyhbd.ttc) (ou choisir des polices qui répondent à vos exigences), puis suivez les étapes ci-dessous :
1. Créez un dossier msyh sous /usr/share/fonts/ et copiez les polices téléchargées dans ce répertoire.
2. 
    ```
    cd /usr/share/fonts/msyh
    sudo mkfontscale
    sudo mkfontdir
    fc-cache
    ```

### 6. Comment remplir le code de timbre pour la synthèse vocale ?
Veuillez vous référer à la documentation du fournisseur de services vocaux, voici les documents pertinents pour ce projet :  
[Documentation OpenAI TTS](https://platform.openai.com/docs/guides/text-to-speech/api-reference), situé dans les options de voix  
[Documentation d'interaction vocale intelligente d'Aliyun](https://help.aliyun.com/zh/isi/developer-reference/overview-of-speech-synthesis), situé dans la liste des timbres - valeur du paramètre voice