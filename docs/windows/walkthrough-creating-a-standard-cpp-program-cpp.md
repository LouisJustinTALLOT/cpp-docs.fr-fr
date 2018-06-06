---
title: 'Procédure pas à pas : Création d’un programme C++ Standard (C++) | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vcfirstapp
- vccreatefirst
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac1fac3c7f96c9f8d718efa54810f4155b1ddac5
ms.sourcegitcommit: c0ffdff538eb961f786809eb547b35846190ee48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34800084"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Procédure pas à pas : Création d’un programme C++ Standard (C++)
Vous pouvez utiliser Visual C++ dans l’environnement de développement intégré (IDE) Visual Studio pour créer des programmes C++ Standard. En suivant les étapes décrites dans cette procédure pas à pas, vous pouvez créer un projet, ajouter un nouveau fichier au projet, modifiez le fichier pour ajouter du code C++, puis compiler et exécuter le programme à l’aide de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 Vous pouvez taper votre propre programme C++ ou utiliser un des exemples de programmes. L’exemple de programme dans cette procédure pas à pas est une application console. Cette application utilise le `set` conteneur dans la bibliothèque C++ Standard.  
  
 Visual C++ est conforme à la norme C++ 2003, avec les exceptions majeures : recherche de nom à deux étapes, spécifications d’exception et l’exportation. En outre, Visual C++ prend en charge plusieurs fonctionnalités C ++ 0 x, par exemple, les expressions lambda, auto, static_assert, références rvalue et les modèles extern.  
  
> [!NOTE]
>  Si la conformité avec la norme est requise, utilisez le **/Za** option du compilateur pour désactiver les extensions Microsoft de la norme. Pour plus d’informations, consultez [/Za, /Ze (désactiver les Extensions de langage)](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour compléter cette procédure pas à pas, vous devez comprendre les notions de base du langage C++.  
  
### <a name="to-create-a-project-and-add-a-source-file"></a>Pour créer un projet et ajouter un fichier source  
  
1.  Créer un projet en pointant sur **nouveau** sur la **fichier** menu, puis en cliquant sur **projet**.  
  
2.  Dans le **Visual C++** volet types de projet, cliquez sur **Windows Desktop**, puis cliquez sur **Application Console Windows**.  
  
3.  Tapez un nom pour le projet.  
  
     Par défaut, la solution qui contient le projet porte le même nom que le projet, mais vous pouvez taper un autre nom. Vous pouvez également taper un autre emplacement pour le projet.  
  
     Cliquez sur **OK** pour créer le projet.  
  
4.  Si **l’Explorateur de solutions** n’apparaît pas, dans le **vue** menu, cliquez sur **l’Explorateur de solutions**.  
  
5.  Ajoutez un nouveau fichier source au projet, comme suit.  
  
    1.  Dans **l’Explorateur de solutions**, avec le bouton droit le **fichiers sources** dossier, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
    2.  Dans le **Code** nœud, cliquez sur **fichier C++ (.cpp)**, tapez un nom pour le fichier, puis cliquez sur **ajouter**.  
  
     Le fichier .cpp apparaît dans le dossier des fichiers sources dans **l’Explorateur de solutions**, et le fichier est ouvert dans l’éditeur Visual Studio.  
  
6.  Dans le fichier dans l’éditeur, tapez un programme C++ valide qui utilise la bibliothèque C++ Standard, ou copiez un des exemples de programmes et collez-le dans le fichier.  
  
7.  Enregistrez le fichier.  
  
8. Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
     Le **sortie** fenêtre affiche des informations sur la progression de la compilation, par exemple, l’emplacement du journal de génération et un message qui indique l’état de la build.  
  
9. Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**.  
  
     Si vous avez utilisé l’exemple de programme, une fenêtre de commande s’affiche et indique si certains entiers se trouvent dans le jeu.  
  
## <a name="next-steps"></a>Étapes suivantes  
 **Précédente :** [dans Visual C++, les Applications de Console](../windows/console-applications-in-visual-cpp.md). **Ensuite :**[procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
