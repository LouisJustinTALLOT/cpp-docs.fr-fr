---
title: Configurer des projets Linux pour utiliser Address Sanitizer
description: Décrit comment configurer des projets Linux C++ dans Visual Studio pour utiliser Address Sanitizer.
ms.date: 09/25/2020
ms.openlocfilehash: 7e68d0af4d2ab27820f894bafc58bed444f141d9
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414194"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Configurer des projets Linux pour utiliser Address Sanitizer

Dans Visual Studio 2019 version 16.1, la prise en charge d’AddressSanitizer (ASan) est intégrée aux projets Linux. Vous pouvez activer ASan pour les projets Linux basés sur MSBuild et pour les projets CMake. Cet outil fonctionne sur les systèmes Linux distants et sur le sous-système Windows pour Linux (WSL).

## <a name="about-asan"></a>À propos d’ASan

ASan est un détecteur d’erreur de mémoire de runtime pour C/C++ qui intercepte les erreurs suivantes :

- Utilisation après libération (référence de pointeur non résolue)
- Dépassement de mémoire tampon au niveau du tas
- Dépassement de mémoire tampon au niveau de la pile
- Utilisation après retour
- Utilisation après la portée
- Bogues liés à l’ordre d’initialisation

Quand ASan détecte une erreur, il arrête l’exécution immédiatement. Si vous exécutez un programme prenant en charge ASan dans le débogueur, vous voyez un message qui décrit le type d’erreur, l’adresse mémoire et l’emplacement dans le fichier source où l’erreur s’est produite :

   ![Message d’erreur ASan](media/asan-error.png)

Vous pouvez également voir la sortie ASan complète (y compris l’endroit où la mémoire endommagée a été alloué ou désallouée) dans le volet de débogage de la fenêtre de sortie.

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Activer ASan pour les projets Linux basés sur MSBuild

> [!NOTE]
> À compter de Visual Studio 2019 version 16,4, AddressSanitizer pour les projets Linux est activé via les propriétés de **projet**propriétés de  >  **configuration**  >  **C/C++**  >  **activer le nettoyage d’adresse**.

Pour activer ASan pour les projets Linux basés sur MSBuild, cliquez avec le bouton droit sur le projet dans l’**Explorateur de solutions**, puis sélectionnez **propriétés**. Ensuite, accédez à **Propriétés de configuration**  >  **C/C++**  >  **désinfecteurs**C/C++. Activé par le biais d’indicateurs de compilateur et d’éditeur de liens, ASan requiert que votre projet soit recompilé pour fonctionner.

![Activer ASan pour un projet MSBuild](media/msbuild-asan-prop-page.png)

Vous pouvez passer des indicateurs d’exécution ASan facultatifs en accédant à **Propriétés de configuration**  >  **débogage**  >  **AddressSanitizer Runtime Flags**. Cliquez sur la flèche vers le bas pour ajouter ou supprimer des indicateurs.

![Configurer les indicateurs d’exécution ASan](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Activer ASan pour les projets CMake Visual Studio

Pour activer ASan pour CMake, cliquez avec le bouton droit sur le fichier CMakeLists.txt dans l’**Explorateur de solutions**, puis choisissez **Paramètres CMake du projet**.

Vérifiez qu’une configuration Linux (par exemple, **Linux-Debug**) est sélectionnée dans le volet gauche de la boîte de dialogue :

![Capture d’écran du volet gauche avec le débogage Linux listé comme l’une des options de configuration.](media/linux-debug-configuration.png)

Les options d’ASan se trouvent sous **Général**. Entrez les indicateurs d’exécution ASan au format « indicateur = valeur », séparés par des espaces. L’interface utilisateur suggère de manière incorrecte en utilisant des points-virgules. Utilisez des espaces ou des points-virgules pour séparer les indicateurs.

![Capture d’écran de l’option d’activation du nettoyage d’adresse montrant certains indicateurs d’heure d’exécution du nettoyage d’adresse.](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Installer les symboles de débogage ASan

Pour activer les diagnostics ASan, vous devez installer ses symboles de débogage (libasan-dbg) sur votre machine Linux distante ou sur l’installation WSL. La version de libasan-dbg que vous chargez dépend de la version de GCC installée sur votre machine Linux :

|**Version d’ASan**|**Version de GCC**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Vous pouvez déterminer la version de GCC que vous avez à l’aide de cette commande :

```bash
gcc --version
```

Pour afficher la version de libasan-dbg dont vous avez besoin, exécutez votre programme, puis examinez le volet **Déboguer** de la fenêtre **Sortie**. La version d’ASan chargée correspond à la version de libasan-dbg nécessaire sur votre machine Linux. Vous pouvez utiliser **Ctrl+F** pour rechercher « libasan » dans la fenêtre. Si vous avez libasan4, par exemple, vous voyez une ligne comme celle-ci :

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Vous pouvez installer les bits de débogage ASan sur les distributions Linux qui utilisent apt avec la commande suivante. Cette commande installe la version 4 :

```bash
sudo apt-get install libasan4-dbg
```

Si ASan est activé, Visual Studio vous invite en haut du volet **Déboguer** de la fenêtre **Sortie** à installer les symboles de débogage ASan.
