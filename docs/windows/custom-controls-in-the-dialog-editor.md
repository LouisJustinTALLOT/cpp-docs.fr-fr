---
title: Contrôles personnalisés dans l’éditeur de boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- Custom Control
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], templates
- custom controls [Visual Studio], dialog boxes
- custom controls [Visual Studio]
- dialog box controls, custom (user) controls
- Dialog editor, custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2c2bca249958e4d25ab5377540525da34802ac04
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880242"
---
# <a name="custom-controls-in-the-dialog-editor"></a>Contrôles personnalisés dans l'Éditeur de boîtes de dialogue
L’éditeur de boîte de dialogue vous permet d’utiliser l’existant « custom » ou des contrôles dans un modèle de boîte de dialogue « utilisateur ».  
  
> [!NOTE]
>  Des contrôles personnalisés dans ce sens ne doivent ne pas être confondues avec les contrôles ActiveX. Contrôles ActiveX étaient parfois appelés contrôles OLE personnalisés. En outre, ne confondez pas ces contrôles avec des contrôles owner-drawn dans Windows.  
  
 Cette fonctionnalité est conçue pour vous permettre d’utiliser des contrôles autres que ceux fournis par Windows. Au moment de l’exécution, le contrôle est associé à une classe de fenêtre (pas identique à une classe C++). Une façon plus courante pour accomplir la même tâche consiste à installer de n’importe quel contrôle, par exemple un contrôle statique, dans votre boîte de dialogue. Puis au moment de l’exécution, dans le [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) de fonction, supprimez ce contrôle et remplacez-le par votre contrôle personnalisé.  
  
 Il s’agit d’une technique ancienne. Aujourd'hui, il est conseillé dans la plupart des cas pour écrire un contrôle ActiveX ou une sous-classe un contrôle commun de Windows.  
  
 Ces contrôles personnalisés, vous êtes limité à :  
  
-   Définition de l’emplacement dans la boîte de dialogue.  
  
-   Taper une légende.  
  
-   Identifiant le nom de la classe du contrôle Windows (code de votre application doit inscrire le contrôle de ce nom).  
  
-   Taper une valeur hexadécimale 32 bits qui définit le style du contrôle.  
  
-   Définir le style étendu.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Spécifications  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Contrôles](../mfc/controls-mfc.md)

