---
title: C++Pages de propriétés de débogage
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 78115a6b-3799-4515-814e-8566b5bdc55d
f1_keywords:
- VC.Project.IVCLocalDebugPageObject.Command
- VC.Project.IVCLocalDebugPageObject.CommandArguments
- VC.Project.IVCLocalDebugPageObject.WorkingDirectory
- VC.Project.IVCLocalDebugPageObject.Attach
- VC.Project.IVCLocalDebugPageObject.DebuggerType
- VC.Project.IVCLocalDebugPageObject.Environment
- VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCLocalDebugPageObject.EnvironmentMerge
- VC.Project.IVCLocalDebugPageObject.SQLDebugging
- VC.Project.IVCLocalDebugPageObject.AmpDefaultAccelerator
- VC.Project.IVCRemoteDebugPageObject.RemoteCommand
- VC.Project.IVCRemoteDebugPageObject.CommandArguments
- VC.Project.IVCRemoteDebugPageObject.WorkingDirectory
- VC.Project.IVCRemoteDebugPageObject.RemoteMachine
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.DebuggerType
- VC.Project.IVCRemoteDebugPageObject.Environment
- VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads
- VC.Project.IVCRemoteDebugPageObject.Attach
- VC.Project.IVCRemoteDebugPageObject.SQLDebugging
- VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory
- VC.Project.IVCRemoteDebugPageObject.AdditionalFiles
- VC.Project.IVCRemoteDebugPageObject.Remote
- VC.Project.IVCRemoteDebugPageObject.AmpDefaultAccelerator
- VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl
- VC.Project.VCDebugSettings.WebBrowser.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.HttpUrl
- VC.Project.IVCWebSvcDebugPageObject.DebuggerType
- VC.Project.IVCWebSvcDebugPageObject.SQLDebugging
ms.openlocfilehash: 5f7a7bc0e2c696365daa38696fde6f1a480644b4
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927736"
---
# <a name="c-debugging-property-pages"></a>C++Pages de propriétés de débogage

Ces pages de propriétés se trouvent**sous propriétés du** >  **projet** > **Configuration Propriétés** > du**débogage**. Choisissez le type de débogueur dans le contrôle déroulant. Pour plus d’informations sur le débogage de C++ code [, consultez Didacticiel : Apprenez à déboguer C++ du code](/visualstudio/debugger/getting-started-with-the-debugger-cpp) à l’aide de Visual Studio et à [Déboguer du code natif](/visualstudio/debugger/debugging-native-code).

## <a name="local-windows-debugger-property-page"></a>Page de propriétés du débogueur Windows local

### <a name="command"></a>Commande

Commande de débogage à exécuter.

### <a name="command-arguments"></a>Arguments de commande

Arguments de ligne de commande à passer à l’application.

### <a name="working-directory"></a>Répertoire de travail

Répertoire de travail de l’application. Par défaut, le répertoire contenant le fichier projet.

### <a name="attach"></a>Attach

Spécifie si le débogueur doit tenter de s’attacher à un processus existant au démarrage du débogage.

### <a name="debugger-type"></a>Type de débogueur

Spécifie le type de débogueur à utiliser. Quand cette option est définie sur auto, le type de débogueur est sélectionné en fonction du contenu du fichier exe.

**Choix**

- **Natif uniquement** -natif uniquement
- **Géré uniquement** -géré uniquement
- **Mixte-mixte**
- Automatique auto
- **Script-script**
- **GPU uniquement (C++ amp)** -GPU uniquement (C++ amp)

### <a name="environment"></a>Environnement

Spécifie l’environnement pour le programme à déboguer, ou les variables à fusionner avec l’environnement existant.

### <a name="debugging-accelerator-type"></a>Type d’accélérateur de débogage

Type d’accélérateur de débogage à utiliser pour déboguer le code GPU. (Disponible lorsque le débogueur GPU est actif.)

### <a name="gpu-default-breakpoint-behavior"></a>Comportement du point d’arrêt par défaut GPU

Définit la fréquence à laquelle le débogueur GPU s’arrête.

**Choix**

- **Arrêter une fois par déformation** en une seule fois par Warp
- **Arrêt pour chaque thread (comportement de l’UC)** -interruption pour chaque thread (comportement de l’UC, par exemple)

### <a name="merge-environment"></a>Fusion de l’environnement

Fusionne les variables d’environnement spécifiées avec l’environnement existant.

### <a name="sql-debugging"></a>Débogage SQL

Attachez le débogueur SQL.

### <a name="amp-default-accelerator"></a>Accélérateur par défaut de l'AMP

Remplacer C++ la sélection d’accélérateur par défaut du amp. La propriété ne s’applique pas lors du débogage de code managé.

## <a name="remote-windows-debugger-property-page"></a>Page de propriétés du débogueur Windows distant

Pour plus d’informations sur le débogage distant, consultez [débogage à distance d' C++ un projet Visual dans Visual Studio](/visualstudio/debugger/remote-debugging-cpp).

### <a name="remote-command"></a>Commande distante

Commande de débogage à exécuter.

### <a name="remote-command-arguments"></a>Arguments de la commande distante

Arguments de ligne de commande à passer à l’application.

### <a name="working-directory"></a>Répertoire de travail

Répertoire de travail de l’application. Par défaut, le répertoire contenant le fichier projet.

### <a name="remote-server-name"></a>Nom du serveur distant

Spécifie un nom de serveur distant.

### <a name="connection"></a>Connexion

Spécifie le type de connexion.

**Choix**

- **À distance avec authentification Windows** -distant avec [authentification Windows](/windows-server/security/windows-authentication/windows-authentication-overview).
- **Distant sans authentification** -distant sans authentification.

### <a name="debugger-type"></a>Type de débogueur

Spécifie le type de débogueur à utiliser. Quand cette option est définie sur auto, le type de débogueur est sélectionné en fonction du contenu du fichier exe.

**Choix**

- **Natif uniquement** -natif uniquement
- **Géré uniquement** -géré uniquement
- **Mixte-mixte**
- Automatique auto
- **Script-script**
- **GPU uniquement (C++ amp)** -GPU uniquement (C++ amp)

### <a name="environment"></a>Environnement

Spécifie l’environnement pour le programme à déboguer, ou les variables à fusionner avec l’environnement existant.

### <a name="debugging-accelerator-type"></a>Type d’accélérateur de débogage

Type d’accélérateur de débogage à utiliser pour déboguer le code GPU. (Disponible lorsque le débogueur GPU est actif.)

### <a name="gpu-default-breakpoint-behavior"></a>Comportement du point d’arrêt par défaut GPU

Définit la fréquence à laquelle le débogueur GPU s’arrête.

**Choix**

- **Arrêter une fois par déformation** en une seule fois par Warp
- **Arrêt pour chaque thread (comportement de l’UC)** -interruption pour chaque thread (comportement de l’UC, par exemple)

### <a name="attach"></a>Attach

Spécifie si le débogueur doit tenter de s’attacher à un processus existant au démarrage du débogage.

### <a name="sql-debugging"></a>Débogage SQL

Attachez le débogueur SQL.

### <a name="deployment-directory"></a>Répertoire de déploiement

Lors du débogage sur un ordinateur distant, si vous souhaitez copier le contenu de la sortie du projet (à l’exception des fichiers PDB) sur l’ordinateur distant, spécifiez le chemin d’accès ici.

### <a name="additional-files-to-deploy"></a>Fichiers supplémentaires à déployer

Lors du débogage sur un ordinateur distant, les fichiers et répertoires spécifiés ici (en plus de la sortie du projet) sont copiés dans le répertoire de déploiement, le cas échéant.

### <a name="deploy-visual-c-debug-runtime-libraries"></a>Déployer les bibliothèques runtime de débogage Visual C++

Spécifie s’il faut déployer les bibliothèques Runtime de débogage pour la plateforme active (Win32, x64 ou ARM).

### <a name="amp-default-accelerator"></a>Accélérateur par défaut de l'AMP

Remplacer C++ la sélection d’accélérateur par défaut du amp. La propriété ne s’applique pas lors du débogage de code managé.

## <a name="web-browser-debugger-property-page"></a>Page de propriétés du débogueur de navigateur Web

### <a name="http-url"></a>URL HTTP

Spécifie l’URL du projet.

### <a name="debugger-type"></a>Type de débogueur

Spécifie le type de débogueur à utiliser. Quand cette option est définie sur auto, le type de débogueur est sélectionné en fonction du contenu du fichier exe.

**Choix**

- **Natif uniquement** -natif uniquement
- **Géré uniquement** -géré uniquement
- **Mixte-mixte**
- Automatique auto
- **Script-script**

## <a name="web-service-debugger-property-page"></a>Page de propriétés du débogueur de service Web

### <a name="http-url"></a>URL HTTP

Spécifie l’URL du projet.

### <a name="debugger-type"></a>Type de débogueur

Spécifie le type de débogueur à utiliser. Quand cette option est définie sur auto, le type de débogueur est sélectionné en fonction du contenu du fichier exe.

**Choix**

- **Natif uniquement** -natif uniquement
- **Géré uniquement** -géré uniquement
- **Mixte-mixte**
- Automatique auto
- **Script-script**

### <a name="sql-debugging"></a>Débogage SQL

Attachez le débogueur SQL.