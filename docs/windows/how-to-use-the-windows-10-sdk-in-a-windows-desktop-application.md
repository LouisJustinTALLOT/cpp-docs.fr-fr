---
title: 'Comment : utiliser Windows 10 SDK dans une Application de bureau Windows | Microsoft Docs'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 937afdb400fff6f0944d8690412257cb66a9c25c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017995"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Procédure : utilisation du Kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows
Lorsque vous créez un projet de bureau Windows classique dans Visual Studio 2017, il est configuré par défaut pour générer avec la version du SDK Windows 10 qui a été installé lors de la charge de travail C++ Desktop a été installé ou mis à jour. Cette version du SDK Windows est compatible avec Windows 7 et versions ultérieures. Consultez [utilisation des en-têtes Windows](/windows/desktop/WinProg/using-the-windows-headers) pour plus d’informations sur le ciblage des versions spécifiques de Windows.

Si vous souhaitez cibler une version antérieure du Kit de développement, vous pouvez ouvrir **projet | Propriétés** et choisissez parmi les autres versions SDK disponibles dans la liste déroulante de Version du Kit de développement logiciel Windows.
  
 À partir de Visual Studio 2015 et le SDK Windows 10, la bibliothèque CRT a été divisée en deux parties, une (ucrtbase) qui contient les fonctions qui sont acceptables pour une utilisation dans les applications Windows universelles et celui qui contient tout le reste (vcruntime140). Étant donné que le Kit de développement logiciel (SDK) Windows 10 contient de nouvelles fonctions, comme de nombreuses fonctions C99, vous devez procéder comme suit pour utiliser ces fonctions. Consultez [Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md).  
  
### <a name="to-target-the-windows-10-sdk"></a>Pour cibler le Kit de développement logiciel (SDK) Windows 10  
  
1.  Assurez-vous que le Kit de développement logiciel (SDK) Windows 10 est installé. Le SDK Windows 10 est installé dans le cadre de la **développement Desktop en C++** charge de travail. Une version autonome est disponible à l’adresse [téléchargements et outils pour Windows 10](https://developer.microsoft.com/windows/downloads).

2.  Ouvrez le menu contextuel du nœud du projet, puis sélectionnez **Recibler la version du Kit de développement logiciel (SDK)**.  
  
     ![Recibler la Version SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     La boîte de dialogue **Examiner les actions de la solution** apparaît.  
  
     ![Passez en revue les Actions de la Solution](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  Dans le **Version de la plateforme cible** liste déroulante, sélectionnez la version du SDK Windows 10 à cibler. Cliquez sur le bouton OK pour appliquer la modification.  
  
     Notez que dans ce contexte, 8.1 fait référence à la version du Kit de développement logiciel (SDK) Windows, qui offre une compatibilité descendante avec Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 et Windows Vista.  
  
     Si cette étape est réussie, le texte suivant s'affiche dans la fenêtre Sortie :  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  Ouvrez les propriétés du projet et, dans la section **Propriétés de configuration, Général** , notez les valeurs de **Version de la plateforme cible Windows**. Changer la valeur ici revient à suivre cette procédure. Consultez [General Property Page (Project)](../ide/general-property-page-project.md).  
  
     ![Cibler la Version de la plateforme](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     Cette action change les valeurs des macros du projet qui incluent des chemins d'accès aux fichiers d'en-tête et aux fichiers de la bibliothèque. Pour voir ce qui a changé, dans le **répertoires Visual C++** section de la **propriétés du projet** boîte de dialogue, choisissez une des propriétés telles que la **répertoires Include**, choisir de Ouvrez la liste déroulante, puis choisissez \<Modifier >. La boîte de dialogue **Répertoires Include** apparaît.  
  
     ![Inclure la boîte de dialogue répertoires](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     Choisissez le **Macros >>** bouton et faites défiler la liste des macros pour les macros du Kit de développement logiciel Windows pour voir toutes les nouvelles valeurs.  
  
     ![Macros de kit de développement logiciel Windows](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  Répétez l'opération pour les autres projets selon vos besoins et régénérez la solution.  
  
### <a name="to-target-the-windows-81-sdk"></a>Pour cibler le Kit de développement logiciel (SDK) Windows 8.1  
  
1.  Ouvrez le menu contextuel du nœud du projet, puis sélectionnez **Recibler la version du Kit de développement logiciel (SDK)**.  
  
2.  Dans le **Version de la plateforme cible** liste déroulante, choisissez **8.1**.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications de bureau Windows (Visual C++)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)