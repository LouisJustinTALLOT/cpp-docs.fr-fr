---
title: Fonctionnement des dépendances d’une Application Visual C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da2aadeba69a8be29627650ba6ef24516098a8e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="understanding-the-dependencies-of-a-visual-c-application"></a>Fonctionnement des dépendances d'une application Visual C++
Pour déterminer les bibliothèques Visual C++ dans une application dépend, vous pouvez afficher les propriétés du projet. (Dans l’Explorateur de solutions, avec le bouton droit sur le projet et choisissez **propriétés** pour ouvrir le **Pages de propriétés** boîte de dialogue.) Vous pouvez également utiliser le Dependency Walker (depends.exe), qui donne une image plus complète des dépendances.  
  
 Dans le **Pages de propriétés** boîte de dialogue, vous pouvez examiner différentes pages sous **propriétés de Configuration** pour comprendre les dépendances. Par exemple, si votre projet utilise les bibliothèques MFC et que vous choisissez **utilisation des MFC**, **utiliser les MFC dans une DLL partagée** sur la **propriétés de Configuration**, **général**  page, votre application au moment de l’exécution dépend de DLL MFC telles que mfc\<version > .dll. Si votre application n’utilise pas MFC, il peut dépendre la bibliothèque CRT si vous choisissez un **de la bibliothèque Runtime** valeur **DLL de débogage multithread (/ MDd)** ou **DLL multithread (/ MD)** sur la **propriétés de Configuration**, **C/C++**, **génération de Code** page.  
  
 Une manière plus complète de déterminer les DLL dont dépend votre application consiste à ouvrir celle-ci à l'aide de Dependency Walker (depends.exe). Vous pouvez télécharger l’outil à partir de la [Dependency Walker](http://go.microsoft.com/fwlink/p/?LinkId=132640) site web.  
  
 À l'aide de depends.exe, vous pouvez examiner la liste des DLL qui sont liées à l'application au moment du chargement, ainsi qu'une liste de ses DLL à chargement différé. Si vous souhaitez obtenir la liste complète des DLL qui sont chargées dynamiquement au moment de l'exécution, vous pouvez utiliser la fonctionnalité de profilage dans depends.exe pour tester l'application jusqu'à ce que vous soyez certain que tous les chemins de code ont été testés. Une fois la session de profilage terminée, depends.exe indique quelles DLL ont été chargées dynamiquement au moment de l'exécution.  
  
 Lorsque vous utilisez depends.exe, notez qu'une DLL peut être dépendante d'une autre DLL ou d'une version d'une DLL spécifique. Vous pouvez utiliser depends.exe soit sur l'ordinateur de développement, soit sur un ordinateur cible. Sur l'ordinateur de développement, depends.exe signale les DLL requises pour prendre en charge une application. Si vous rencontrez des problèmes pour exécuter une application sur un ordinateur cible, vous pouvez copier depends.exe sur celui-ci, puis ouvrir l'application dans l'outil afin que vous puissiez déterminer quelles DLL obligatoires manquent ou sont incorrectes.  
  
 Lorsque vous disposez de la liste complète des DLL dont dépend votre application, vous pouvez déterminer celles que vous devez redistribuer avec votre application lors du déploiement vers un autre ordinateur. Dans la plupart des cas, vous n’êtes pas obligé de redistribuer les DLL système, mais vous devrez peut-être redistribuer les DLL des bibliothèques Visual C++. Pour plus d’informations, consultez [détermination des DLL à redistribuer](../ide/determining-which-dlls-to-redistribute.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’Applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)