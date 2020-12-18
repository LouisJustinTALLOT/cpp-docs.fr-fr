---
title: 'vcpkg : gestionnaire de package C++ pour Windows, Linux et macOS'
description: vcpkg est un gestionnaire de package en ligne de commande qui simplifie grandement l’acquisition et l’installation de bibliothèques C++ Open source sur Windows, macOS et Linux.
ms.custom: contperf-fy21q2
ms.date: 12/11/2020
ms.topic: overview
ms.technology: cpp-ide
ms.openlocfilehash: f937f1df718bf8dfcc0ae5166d8b9eb671d2d8ab
ms.sourcegitcommit: 2b2c3fa9244e31db35ea33554dea0efcab490f3c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97682464"
---
# <a name="vcpkg-a-c-package-manager-for-windows-linux-and-macos"></a>vcpkg : gestionnaire de package C++ pour Windows, Linux et macOS

vcpkg est un gestionnaire de package en ligne de commande multiplateforme pour les bibliothèques C et C++. Il simplifie l’acquisition et l’installation de bibliothèques tierces sur Windows, Linux et macOS. Si votre projet utilise des bibliothèques tierces, nous vous recommandons d’utiliser vcpkg pour les installer. vcpkg prend en charge les bibliothèques open source et propriétaires. La compatibilité de toutes les bibliothèques du catalogue Windows vcpkg a été testée avec Visual Studio 2015, Visual Studio 2017 et Visual Studio 2019. Entre les catalogues Windows et Linux/macOS, vcpkg prend désormais en charge des milliers de bibliothèques. La communauté C++ ajoute régulièrement des bibliothèques aux catalogues.

## <a name="how-to-get-and-use-vcpkg"></a>Obtention et utilisation de vcpkg

Installez vcpkg en créant un clone local à partir de son GitHub référentiel [https://github.com/Microsoft/vcpkg](https://github.com/Microsoft/vcpkg) . Exécutez ensuite le script vcpkg-Bootstrapper pour le configurer. Pour obtenir des instructions d’installation détaillées, voir [install vcpkg](install-vcpkg.md). Pour intégrer vcpkg à votre environnement de développement Visual Studio ou Visual Studio Code, consultez [intégrer vcpkg](integrate-vcpkg.md). Ensuite, pour utiliser vcpkg pour installer ou mettre à jour une bibliothèque, consultez [gérer les bibliothèques avec vcpkg](manage-libraries-with-vcpkg.md). Pour plus d’informations sur les commandes vcpkg, consultez Référence de la [ligne de commande vcpkg](vcpkg-command-line-reference.md).

## <a name="how-vcpkg-works"></a>Fonctionnement de vcpkg

Le projet vcpkg est open-source, disponible sur GitHub. Une *copie ou une* copie locale du référentiel vcpkg contient l’exécutable vcpkg et un *catalogue*, une liste des packages qui décrivent une bibliothèque et ses options. Chaque package comprend un ou plusieurs *ports*, des informations sur la façon d’obtenir et de générer la bibliothèque à partir de sources, ou de télécharger une version binaire pour un environnement cible spécifique. Quand vous utilisez vcpkg pour installer une bibliothèque, il utilise le package et les informations de port pour télécharger et générer une copie locale de la bibliothèque dans un sous-répertoire du répertoire vcpkg, prêt à être utilisé.

Quand une bibliothèque est disponible sous forme de source, vcpkg télécharge les sources au lieu des fichiers binaires. Elle compile ces sources à l’aide de la version la plus récente du compilateur C ou C++ et des outils qu’elle peut trouver. Pour la compatibilité ABI C++, il est important que le code de votre application et les bibliothèques que vous utilisez soient compilés par la même version du même compilateur. En utilisant vcpkg, vous éliminez ou au moins réduisez considérablement les risques de binaires incompatibles et les problèmes qu’ils peuvent engendrer. Dans les équipes qui normalisent une version spécifique d’un compilateur, un membre de l’équipe peut utiliser vcpkg pour télécharger des sources et compiler un ensemble de fichiers binaires. Il est inefficace de faire en sorte que tous les membres d’une équipe téléchargent et créent des bibliothèques communes. Un membre de l’équipe peut utiliser la **`vcpkg export`** commande pour créer un fichier zip commun des fichiers binaires et des en-têtes, ou un package NuGet. Ensuite, il est facile de la partager avec d’autres membres de l’équipe.

## <a name="customize-vcpkg-instances-for-different-targets"></a>Personnaliser les instances vcpkg pour différentes cibles

Vous pouvez cloner plusieurs copies, ou *instances*, de vcpkg sur votre ordinateur et personnaliser chacune d’elles à des fins spécifiques. Dans chaque instance, vous pouvez installer différentes bibliothèques ou même des versions de bibliothèques différentes de celles figurant dans le catalogue public. Chaque instance peut être définie de façon à produire une collection de bibliothèques personnalisée, à l’aide de vos options de compilateur préférées. Chaque instance est un environnement autonome avec sa propre copie de vcpkg.exe qui ne fonctionne que sur sa propre hiérarchie. vcpkg n’est ajouté à aucune variable d’environnement et n’a aucune dépendance vis-à-vis du Registre Windows ou de Visual Studio.

Vous pouvez également créer un clone vcpkg contenant des bibliothèques privées dans la collection ports. Vous pouvez ajouter un port qui télécharge vos fichiers binaires et en-têtes prédéfinis. Ensuite, écrivez un fichier *portfile. cmake* qui copie simplement ces fichiers à l’emplacement préféré.

## <a name="the-vcpkg-folder-hierarchy"></a>La hiérarchie des dossiers vcpkg

Toutes les fonctionnalités et données vcpkg sont autonomes dans une hiérarchie d’annuaire unique par instance. Il n’existe pas de paramètre de Registre ni de variable d’environnement. Vous pouvez avoir un nombre quelconque d’instances de vcpkg sur un ordinateur, et elles n’interfèrent pas les unes avec les autres.

Une instance de vcpkg comporte les éléments suivants :

- *`buildtrees`* -Contient les sous-dossiers des sources à partir desquelles chaque bibliothèque est créée.
- *`docs`* -documentation et exemples.
- *`downloads`* -Copies mises en cache de tous les outils ou sources téléchargés. vcpkg recherche d’abord ici quand vous exécutez la commande d’installation.
- *`installed`* -Contient les en-têtes et les binaires de chaque bibliothèque installée. Lorsque vous intégrez à Visual Studio, vous lui dites essentiellement d’ajouter ce dossier à ses chemins de recherche.
- *`packages`* -Dossier interne pour la mise en lots entre les installations.
- *`ports`* -Les fichiers qui décrivent chaque bibliothèque dans le catalogue, sa version et l’emplacement où la télécharger. Le cas échéant, vous pouvez ajouter vos propres ports.
- *`scripts`* -Scripts (CMake, PowerShell) utilisés par vcpkg.
- *`toolsrc`* -Code source C++ pour vcpkg et les composants associés.
- *`triplets`* -Contient les paramètres pour chaque plateforme cible prise en charge (par exemple, x86-Windows ou x64-UWP).

## <a name="telemetry"></a>Télémétrie

vcpkg collecte les données d’utilisation afin de nous aider à améliorer votre expérience. Les données collectées par Microsoft sont anonymes. Vous pouvez refuser la télémétrie en réexécutant le **`bootstrap-vcpkg.bat`** script ou à l' **`bootstrap-vcpkg.sh`** aide de l' **`-disableMetrics`** option. Ou, transmettez l' **`--disable-metrics`** option à vcpkg sur la ligne de commande. Vous pouvez également désactiver les métriques en définissant la `VCPKG_DISABLE_METRICS` variable d’environnement.

## <a name="send-feedback-about-vcpkg"></a>Envoyer des commentaires à propos de vcpkg

Utilisez la **`vcpkg contact --survey`** commande pour envoyer des commentaires à Microsoft sur vcpkg, notamment des rapports de bogues et des suggestions de fonctionnalités. Pour plus d’informations, consultez Référence de la [ligne de commande vcpkg](vcpkg-command-line-reference.md).

## <a name="see-also"></a>Voir aussi

[vcpkg sur GitHub](https://github.com/Microsoft/vcpkg)\
[Installer vcpkg](install-vcpkg.md)\
[Intégrer vcpkg](integrate-vcpkg.md)\
[Gérer les bibliothèques avec vcpkg](manage-libraries-with-vcpkg.md)\
[informations de référence sur la ligne de commande vcpkg](vcpkg-command-line-reference.md)\
[Démarrage rapide](https://github.com/microsoft/vcpkg/blob/master/docs/index.md)\
[Forum aux questions](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
