---
title: "Comment : utiliser les fenêtres 10 SDK dans une Application de bureau Windows | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f5e6f09b371c4d295b4bcdff469396a2671d22a
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Procédure : utilisation du Kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows
Lorsque vous créez un projet de bureau Windows classique dans Visual Studio 2017, il est configuré par défaut pour générer avec la version du SDK Windows 10 qui a été installé lors de la charge de travail de bureau C++ a été installé ou mis à jour. Cette version du SDK Windows est compatible avec toutes les versions récentes de Windows. Si vous souhaitez cibler une version antérieure du Kit de développement, vous pouvez ouvrir le projet | Propriétés et choisissez parmi les autres versions de kit de développement logiciel disponibles dans la liste déroulante Version du Kit de développement logiciel Windows.  
  
 À partir de Visual Studio 2015 et le SDK Windows 10, la bibliothèque CRT a été séparée en deux parties, une (ucrtbase) qui contient les fonctions qui sont acceptables pour une utilisation dans les applications Windows universelles et celui qui contient tout le reste (vcruntime140). Étant donné que le Kit de développement logiciel (SDK) Windows 10 contient de nouvelles fonctions, comme de nombreuses fonctions C99, vous devez procéder comme suit pour utiliser ces fonctions. Consultez [Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md).  
  
### <a name="to-target-the-windows-10-sdk"></a>Pour cibler le Kit de développement logiciel (SDK) Windows 10  
  
1.  Assurez-vous que le Kit de développement logiciel (SDK) Windows 10 est installé. Le SDK Windows 10 est installé dans le cadre de la [outils pour Windows 10](http://go.microsoft.com/fwlink/p/?linkid=617631).  
  
2.  Ouvrez le menu contextuel du nœud du projet, puis sélectionnez **Recibler la version du Kit de développement logiciel (SDK)**.  
  
     ![Recibler la Version du Kit de développement logiciel](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     La boîte de dialogue **Examiner les actions de la solution** apparaît.  
  
     ![Passez en revue les Actions de la Solution](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  Dans le **Version de la plateforme cible** liste déroulante, sélectionnez la version du SDK Windows 10 à cibler. Cliquez sur le bouton OK pour appliquer la modification.  
  
     Notez que dans ce contexte, 8.1 fait référence à la version du Kit de développement logiciel (SDK) Windows, qui offre une compatibilité descendante avec Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 et Windows Vista.  
  
     Si cette étape est réussie, le texte suivant s'affiche dans la fenêtre Sortie :  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  Ouvrez les propriétés du projet et, dans la section **Propriétés de configuration, Général** , notez les valeurs de **Version de la plateforme cible Windows**. Changer la valeur ici revient à suivre cette procédure. Consultez [General Property Page (Project)](../ide/general-property-page-project.md).  
  
     ![Cibler la Version de la plateforme](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     Cette action change les valeurs des macros du projet qui incluent des chemins d'accès aux fichiers d'en-tête et aux fichiers de la bibliothèque. Pour voir ce qui a été modifié, dans la section répertoires Visual C++ de la boîte de dialogue Propriétés du projet, choisissez l’une des propriétés telles que les répertoires Include, ouvrez la liste déroulante, puis choisissez \<Modifier >. La boîte de dialogue **Répertoires Include** apparaît.  
  
     ![Inclure la boîte de dialogue répertoires](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     Choisissez le **Macros >>** bouton et faites défiler la liste des macros aux macros du Kit de développement logiciel Windows pour voir toutes les nouvelles valeurs.  
  
     ![Macros du Kit de développement logiciel Windows](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  Répétez l'opération pour les autres projets selon vos besoins et régénérez la solution.  
  
### <a name="to-target-the-windows-81-sdk"></a>Pour cibler le Kit de développement logiciel (SDK) Windows 8.1  
  
1.  Ouvrez le menu contextuel du nœud du projet, puis sélectionnez **Recibler la version du Kit de développement logiciel (SDK)**.  
  
2.  Dans la liste déroulante Version de la plateforme cible, choisissez 8.1.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications de bureau Windows (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)
