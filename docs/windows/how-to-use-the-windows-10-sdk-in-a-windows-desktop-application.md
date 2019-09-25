---
title: 'Procédure : Utiliser le kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: 8dbf18d24c0369507743c3c1da624838f9ab4703
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69513823"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>Procédure : Utiliser le kit de développement logiciel (SDK) Windows 10 dans une application de bureau Windows

Lorsque vous créez un projet de bureau Windows classique dans Visual Studio 2017, il est configuré par défaut pour être généré avec la version du kit de développement logiciel (SDK) Windows C++ 10 qui a été installée lors de l’installation ou de la dernière mise à jour de la charge de travail du bureau. Cette version du SDK Windows est compatible avec Windows 7 et versions ultérieures. Pour plus d’informations sur le ciblage de versions spécifiques de Windows, consultez [utilisation des en-têtes Windows](/windows/win32/WinProg/using-the-windows-headers) .

Si vous souhaitez cibler une version antérieure du kit de développement logiciel (SDK), vous pouvez ouvrir le **projet | Propriétés** et choisissez parmi les autres versions du kit de développement logiciel (SDK) disponibles dans la liste déroulante SDK Windows version.

À compter de Visual Studio 2015 et du kit de développement logiciel (SDK) Windows 10, la bibliothèque CRT a été divisée en deux parties, une (ucrtbase) qui contient les fonctions qui sont acceptables pour une utilisation dans les applications Windows universelles, et une qui contient tout le reste (vcruntime140). Étant donné que le Kit de développement logiciel (SDK) Windows 10 contient de nouvelles fonctions, comme de nombreuses fonctions C99, vous devez procéder comme suit pour utiliser ces fonctions. Consultez [CRT Library Features](../c-runtime-library/crt-library-features.md).

### <a name="to-target-the-windows-10-sdk"></a>Pour cibler le Kit de développement logiciel (SDK) Windows 10

1. Assurez-vous que le Kit de développement logiciel (SDK) Windows 10 est installé. Le kit de développement logiciel (SDK) Windows 10 est installé dans le cadre du **développement bureautique avec C++**  charge de travail. Une version autonome est disponible à l’adresse [téléchargements et outils pour Windows 10](https://developer.microsoft.com/windows/downloads).

2. Ouvrez le menu contextuel du nœud du projet, puis sélectionnez **Recibler la version du Kit de développement logiciel (SDK)** .

   ![Recibler la version du SDK](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   La boîte de dialogue **Examiner les actions de la solution** apparaît.

   ![Examiner les actions] de la solution (../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. Dans la liste déroulante version de la **plateforme cible** , choisissez la version du kit de développement logiciel (SDK) Windows 10 que vous souhaitez cibler. Cliquez sur le bouton OK pour appliquer la modification.

   Notez que dans ce contexte, 8.1 fait référence à la version du Kit de développement logiciel (SDK) Windows, qui offre une compatibilité descendante avec Windows 8, Windows Server 2012, Windows 7, Windows Server 2008 et Windows Vista.

   Si cette étape est réussie, le texte suivant s'affiche dans la fenêtre Sortie :

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. Ouvrez les propriétés du projet et, dans la section **Propriétés de configuration, Général** , notez les valeurs de **Version de la plateforme cible Windows**. Changer la valeur ici revient à suivre cette procédure. Consultez [General Property Page (Project)](../build/reference/general-property-page-project.md).

   ![Version de la plateforme cible](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   Cette action change les valeurs des macros du projet qui incluent des chemins d'accès aux fichiers d'en-tête et aux fichiers de la bibliothèque. Pour voir ce qui a été modifié, dans la section **répertoires visuels C++**  de la boîte de dialogue **Propriétés du projet** , choisissez l’une des propriétés, telles que les **répertoires Include**, choisissez d’ouvrir la liste déroulante, puis choisissez \<modifier les >. La boîte de dialogue **Répertoires Include** apparaît.

   ![Boîte de dialogue répertoires Include](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   Choisissez le bouton **macros > >** , puis faites défiler la liste des macros vers le SDK Windows macros pour afficher toutes les nouvelles valeurs.

   ![Macros SDK Windows](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. Répétez l'opération pour les autres projets selon vos besoins et régénérez la solution.

### <a name="to-target-the-windows-81-sdk"></a>Pour cibler le Kit de développement logiciel (SDK) Windows 8.1

1. Ouvrez le menu contextuel du nœud du projet, puis sélectionnez **Recibler la version du Kit de développement logiciel (SDK)** .

2. Dans la liste déroulante version de la **plateforme cible** , choisissez **8,1**.

## <a name="see-also"></a>Voir aussi

[Applications de bureau Windows ( C++visuel)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)