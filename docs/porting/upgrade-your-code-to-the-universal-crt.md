---
title: Mettre à niveau votre code vers le CRT universel | Microsoft Docs
ms.custom: ''
ms.date: 03/31/2017
ms.topic: conceptual
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f53ee06b4d964307cdcc294e415f6e470eb176f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401056"
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>Mettre à niveau votre code vers le CRT universel

Dans Visual Studio 2015, la bibliothèque Microsoft Runtime C (CRT) a été refactorisée. La bibliothèque standard C, les extensions POSIX et les fonctions, macros et variables globales spécifiques à Microsoft ont été déplacées vers une nouvelle bibliothèque, à savoir la bibliothèque Runtime C universelle (CRT universel ou UCRT). Les composants spécifiques au compilateur du CRT ont été déplacés vers une nouvelle bibliothèque vcruntime.  
  
UCRT est désormais un composant Windows fourni avec Windows 10. L’UCRT prend en charge une ABI stable basée sur les conventions d’appel C et est conforme à la norme ISO C99, à quelques exceptions près. Elle n’est plus liée à une version spécifique du compilateur. Vous pouvez utiliser l’UCRT sur n’importe quelle version de Windows prise en charge par Visual Studio 2015 ou Visual Studio 2017. Ainsi, vous n’avez plus besoin de mettre à jour vos builds pour cibler une nouvelle version du CRT avec chaque mise à niveau de Visual Studio.  
  
Grâce à cette refactorisation, les noms ou les emplacements de nombreux fichiers d’en-tête CRT, fichiers de bibliothèque, fichiers redistribuables et les méthodes de déploiement requises pour votre code ont été modifiés. En outre, l’ajout ou la modification de nombreuses fonctions et macros dans l’UCRT a entraîné une amélioration de la conformité aux normes. Pour tirer parti de ces modifications, vous devez mettre à jour vos systèmes de génération de projet et de code existants.  
  
## <a name="where-to-find-the-universal-crt-files"></a>Où trouver les fichiers du CRT universel

En tant que composant Windows, les fichiers et en-têtes de la bibliothèque UCRT font désormais partie du SDK Windows. Quand vous installez Visual Studio, les parties du SDK Windows nécessaires pour utiliser l’UCRT sont également installées. Le programme d’installation de Visual Studio ajoute les emplacements des fichiers DLL, des bibliothèques et des en-têtes UCRT aux chemins par défaut utilisés par le système de génération de projet Visual Studio. Quand vous mettez à jour vos projets Visual C++, s’ils utilisent les paramètres de projet par défaut, l’IDE détecte automatiquement les nouveaux emplacements des fichiers d’en-tête, et l’éditeur de liens utilise automatiquement les nouvelles bibliothèques vcruntime et UCRT par défaut. De même, si vous utilisez une invite de commandes développeur pour effectuer des générations à partir d’une ligne de commande, les variables d’environnement qui contiennent des chemins d’en-têtes et de bibliothèques sont mises à jour et sont automatiquement opérationnelles.  
  
Les fichiers d’en-tête de la bibliothèque standard C se trouvent désormais dans le SDK Windows, au sein d’un dossier include rattaché à un répertoire spécifique à la version du SDK. Un emplacement standard pour les fichiers d’en-tête est le répertoire Program Files ou Program Files (x86) sous Windows Kits\\10\\Include\\_version_sdk_\\ucrt, où _version_sdk_ correspond à une version ou mise à jour Windows, par exemple, 10.0.14393.0 pour la mise à jour anniversaire Windows 10.   
  
Les bibliothèques statiques UCRT et les bibliothèques de liens dynamiques stub se trouvent dans le répertoire Program Files ou Program Files (x86) sous Windows Kits\\10\\Lib\\_version_sdk_\\ucrt\\_architecture_, où _architecture_ est ARM, x86 ou X64. Les bibliothèques statiques commerciales et de débogage sont libucrt.lib et libucrtd.lib, tandis que les bibliothèques pour les DLL UCRT sont ucrt.lib et ucrtd.lib.  
  
Les DLL UCRT commerciales et de débogage se trouvent dans des emplacements distincts. Les DLL commerciales sont redistribuables. Elles se trouvent dans le répertoire Program Files ou Program Files (x86) sous Windows Kits\\10\\Redist\\ucrt\\DLLs\\_architecture_\. Les bibliothèques UCRT de débogage ne sont pas redistribuables. Elles se trouvent dans le répertoire Program Files ou Program Files (x86) sous Windows Kits\\10\\bin\\_architecture_\\ucrt.   

La bibliothèque de prise en charge du runtime spécifique au compilateur C et C++, **vcruntime**, contient le code nécessaire pour prendre en charge le démarrage du programme et les fonctionnalités telles que la gestion des exceptions et les intrinsèques. La bibliothèque et ses fichiers d’en-tête se trouvent toujours dans le dossier spécifique à la version Microsoft Visual Studio dans le répertoire Program Files ou Program files (x86). Dans Visual Studio 2017, les en-têtes se trouvent sous Microsoft Visual Studio\\2017\\_édition_\\VC\\Tools\\MSVC\\_version_bib_\\include, tandis que les bibliothèques de liens se trouvent sous Microsoft Visual Studio\\2017\\_édition_\\VC\\Tools\\MSVC\\_version_bib_\\lib\\_architecture_, où _édition_ est l’édition de Visual Studio installée, _version_bib_ la version des bibliothèques et _architecture_ l’architecture du processeur. Des bibliothèques de liens pour OneCore et Store sont également présentes dans le dossier des bibliothèques. Les versions commerciale et de débogage de la bibliothèque statique sont libvcruntime.lib et libvcruntimed.lib. Les bibliothèques stub commerciale et de débogage de liens dynamiques sont vcruntime.lib et vcruntimed.lib, respectivement.  
  
Quand vous mettez à jour vos projets Visual C++, si vous avez affecté à la propriété **Éditeur de liens** **Ignorer toutes les bibliothèques par défaut** du projet la valeur **Oui**, ou si vous utilisez l’option `/NODEFAULTLIB` de l’éditeur de liens sur la ligne de commande, vous devez mettre à jour votre liste de bibliothèques pour inclure les nouvelles bibliothèques refactorisées. Remplacez l’ancienne bibliothèque CRT, par exemple, libcmt.lib, libcmtd.lib, msvcrt.lib ou msvcrtd.lib, par les bibliothèques refactorisées équivalentes. Pour plus d’informations sur les bibliothèques spécifiques à utiliser, consultez [Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md).  
  
## <a name="deployment-and-redistribution-of-the-universal-crt"></a>Déploiement et redistribution du CRT universel
  
L’UCRT étant à présent un composant du système d’exploitation Microsoft Windows, il est inclus dans le cadre du système d’exploitation dans Windows 10 et est disponible par le biais de Windows Update pour les anciens systèmes d’exploitation allant de Windows Vista à Windows 8.1. Une version redistribuable est disponible pour Windows XP. En tant que composant du système d’exploitation, les mises à jour et maintenance de l’UCRT sont gérées par Windows Update indépendamment des versions du compilateur de Microsoft C++ et de Visual Studio. L’UCRT étant un composant Windows, nous vous recommandons vivement de déployer l’UCRT pour votre application de manière centralisée ; la sécurité s’en trouvera améliorée, les mises à jour simplifiées et la taille d’image réduite.  
  
Vous pouvez utiliser l’UCRT sur n’importe quelle version de Windows prise en charge par Visual Studio 2015 ou Visual Studio 2017. Vous pouvez la redistribuer à l’aide d’un package vcredist pour les versions prises en charge de Windows distinctes de Windows 10. Les packages vcredist incluent les composants UCRT et les installent automatiquement sur les systèmes d’exploitation Windows qui en sont dépourvus par défaut. Pour plus d’informations, consultez [Redistribution des fichiers Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
Le déploiement local de l’application de l’UCRT est pris en charge, bien que non recommandé pour des raisons de performances et de sécurité. Les DLL pour un déploiement local de l’application sont incluses dans le cadre du SDK Windows, dans le sous-répertoire **redist**. Les DLL requises incluent ucrtbase.dll et un jeu de DLL de type **redirecteur APISet** nommé -ms-win-_sous-ensemble_.dll. Comme le jeu de DLL requis varie d’un système d’exploitation à l’autre, nous vous recommandons d’inclure toutes les DLL quand vous utilisez le déploiement local de l’application. Pour plus de détails et mises en garde concernant le déploiement local de l’application, consultez [Déploiement dans Visual C++](../ide/deployment-in-visual-cpp.md).  
  
## <a name="changes-to-the-universal-crt-functions-and-macros"></a>Modifications apportées aux macros et fonctions du CRT universel  

De nombreuses fonctions ont été ajoutées ou mises à jour dans l’UCRT pour améliorer la conformité à la norme ISO C99 et pour résoudre les problèmes liés à la sécurité et à la qualité du code. Dans certains cas, des modifications de la bibliothèque avec rupture ont été nécessaires. Si votre code se compilait correctement quand vous utilisiez une version antérieure du CRT, mais qu’il se bloque quand vous le compilez à l’aide de l’UCRT, vous devez le modifier pour qu’il tire parti de ces fonctionnalités et mises à jour. Pour obtenir une liste détaillée des modifications et mises à jour avec rupture apportées à la bibliothèque CRT et disponibles dans le CRT universel, consultez la section [Bibliothèque Runtime C (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) de l’historique des modifications de Visual C++. Elle inclut une liste des en-têtes et fonctions affectés que vous pouvez utiliser pour identifier les modifications nécessaires dans votre code.  
  
## <a name="see-also"></a>Voir aussi  

[Guide du portage et de la mise à niveau de Visual C++](visual-cpp-porting-and-upgrading-guide.md)<br/>
[Vue d’ensemble des problèmes de mise à niveau potentiels (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Mise à niveau de projets à partir de versions antérieures de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Historique des modifications de Visual C++ entre 2003 et 2015](visual-cpp-change-history-2003-2015.md)<br/>
[Améliorations de la conformité de C++ dans Visual Studio 2017](../cpp-conformance-improvements-2017.md)  