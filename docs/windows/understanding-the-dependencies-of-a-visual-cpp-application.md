---
title: Fonctionnement des dépendances d'une application Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], dependencies
- Dependency Walker
- dependencies [C++], application deployment and
- deploying applications [C++], dependencies
- DUMPBIN utility
- DLLs [C++], dependencies
- depends.exe
- libraries [C++], application deployment issues
ms.assetid: 62a44c95-c389-4c5f-82fd-07d7ef09dbf9
ms.openlocfilehash: 92db11778de7d31bbab67e649cd58e264da331e6
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786319"
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Fonctionnement des dépendances d'une application Visual C++

Pour déterminer les bibliothèques Visual C++ dont dépend une application, vous pouvez voir les propriétés du projet. (Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet, puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **Pages de propriétés**.) Sur Windows 8 et versions antérieures, vous pouvez également utiliser le Dependency Walker (depends.exe), ce qui donne une image plus complète des dépendances. Pour les versions plus récentes de Windows le [lucasg/dépendances](https://github.com/lucasg/Dependencies) outil fournit une fonctionnalité similaire (c’est un outil tiers ne pas garanti par Microsoft).

Dans la boîte de dialogue **Pages de propriétés**, vous pouvez examiner différentes pages sous **Propriétés de configuration** pour comprendre les dépendances. Par exemple, si votre projet utilise les bibliothèques MFC et que vous choisissez **Utilisation des MFC**, **Utiliser les MFC dans une DLL partagée** dans la page **Propriétés de configuration**, **Général**, votre application au moment de l’exécution dépend d’une DLL MFC comme mfc\<version>.dll. Si votre application n’utilise pas MFC, elle peut encore dépendre de la bibliothèque CRT si vous choisissez pour la **Bibliothèque Runtime** la valeur **DLL de débogage multithread (/MDd)** ou **DLL multithread (/MD)** dans la page **Propriétés de configuration**, **C/C++**, **Génération de code**.

À l'aide de depends.exe, vous pouvez examiner la liste des DLL qui sont liées à l'application au moment du chargement, ainsi qu'une liste de ses DLL à chargement différé. Si vous souhaitez obtenir la liste complète des DLL qui sont chargées dynamiquement au moment de l'exécution, vous pouvez utiliser la fonctionnalité de profilage dans depends.exe pour tester l'application jusqu'à ce que vous soyez certain que tous les chemins de code ont été testés. Une fois la session de profilage terminée, depends.exe indique quelles DLL ont été chargées dynamiquement au moment de l'exécution.

Lorsque vous utilisez depends.exe, notez qu'une DLL peut être dépendante d'une autre DLL ou d'une version d'une DLL spécifique. Vous pouvez utiliser depends.exe soit sur l'ordinateur de développement, soit sur un ordinateur cible. Sur l'ordinateur de développement, depends.exe signale les DLL requises pour prendre en charge une application. Si vous rencontrez des problèmes pour exécuter une application sur un ordinateur cible, vous pouvez copier depends.exe sur celui-ci, puis ouvrir l'application dans l'outil afin que vous puissiez déterminer quelles DLL obligatoires manquent ou sont incorrectes.

Lorsque vous disposez de la liste complète des DLL dont dépend votre application, vous pouvez déterminer celles que vous devez redistribuer avec votre application lors du déploiement vers un autre ordinateur. Dans la plupart des cas, vous n’avez pas besoin de redistribuer les DLL système, mais vous devez peut-être redistribuer les DLL des bibliothèques Visual C++. Pour plus d’informations, consultez [Détermination des DLL à redistribuer](determining-which-dlls-to-redistribute.md).

## <a name="see-also"></a>Voir aussi

[Déploiement des applications de bureau](deploying-native-desktop-applications-visual-cpp.md)
