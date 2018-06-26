---
title: Ajout de plusieurs vues à un seul Document | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c48f4525c01149840ca74eee249263eac27c24cf
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928699"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Ajout de plusieurs vues à un seul document
Dans une application de l’interface monodocument (SDI) créée avec la bibliothèque Microsoft Foundation classes (MFC), chaque type de document est associé à un seul type de vue. Dans certains cas, il est souhaitable que la possibilité de basculer l’affichage actuel d’un document avec une nouvelle vue.  
  
> [!TIP]
>  Pour obtenir des procédures supplémentaires sur l’implémentation de plusieurs vues pour un seul document, consultez [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) et [collecter](../visual-cpp-samples.md) exemple MFC.  
  
 Vous pouvez implémenter cette fonctionnalité en ajoutant un nouvel `CView`-dérivée la classe et du code supplémentaire pour basculer les vues dynamiquement à une application MFC existante.  
  
 Les étapes sont les suivantes :  
  
-   [Modifiez la classe d’Application existant](#vcconmodifyexistingapplicationa1)  
  
-   [Créer et modifier la nouvelle classe d’affichage](#vcconnewviewclassa2)  
  
-   [Créer et attacher la nouvelle vue](#vcconattachnewviewa3)  
  
-   [Implémenter la fonction d’échange](#vcconswitchingfunctiona4)  
  
-   [Ajouter la prise en charge pour le basculement de la vue](#vcconswitchingtheviewa5)  
  
 Le reste de cette rubrique suppose que les éléments suivants :  
  
-   Le nom de la `CWinApp`-objet dérivé est `CMyWinApp`, et `CMyWinApp` est déclaré et défini dans *MYWINAPP. H* et *MYWINAPP. CPP*.  
  
-   `CNewView` est le nom de la nouvelle `CView`-objet, dérivé et `CNewView` est déclaré et défini dans *NEWVIEW. H* et *NEWVIEW. CPP*.  
  
##  <a name="vcconmodifyexistingapplicationa1"></a> Modifiez la classe d’Application existant  
 Pour basculer entre les vues de l’application, vous devez modifier la classe d’application en ajoutant des variables membres pour stocker les vues et une méthode pour passer.  
  
 Ajoutez le code suivant à la déclaration de `CMyWinApp` dans *MYWINAPP. H*:  
  
 [!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]  
  
 Les nouvelles variables membres, `m_pOldView` et `m_pNewView`, pointez sur l’affichage actuel et celui qui vient d’être créé. La nouvelle méthode (`SwitchView`) bascule les vues lorsqu’il est demandé par l’utilisateur. Le corps de la méthode est décrite plus loin dans cette rubrique dans [implémenter la fonction de basculement](#vcconswitchingfunctiona4).  
  
 La dernière modification à la classe de l’application nécessite un fichier d’en-tête qui définit un message Windows (**WM_INITIALUPDATE**) qui est utilisée dans la fonction d’échange.  
  
 Insérez la ligne suivante dans la section include de *MYWINAPP. CPP*:  
  
 [!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]  
  
 Enregistrez vos modifications et continuer à l’étape suivante.  
  
##  <a name="vcconnewviewclassa2"></a> Créer et modifier la nouvelle classe d’affichage  
 Création de la classe d’affichage est très simple à l’aide de la **nouvelle classe** commande disponible à partir de l’affichage de classes. La seule exigence à cette classe est qu’il dérive `CView`. Ajouter cette classe nouvelle à l’application. Pour plus d’informations sur l’ajout d’une nouvelle classe au projet, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md).  
  
 Une fois que vous avez ajouté la classe au projet, vous devez modifier l’accessibilité de certains membres de classe de vue.  
  
 Modifier *NEWVIEW. H* en modifiant le spécificateur d’accès à partir de **protégé** à **public** pour le constructeur et le destructeur. Ainsi, la classe d’être créés et détruits de façon dynamique et de modifier l’apparence de la vue avant qu’il soit visible.  
  
 Enregistrez vos modifications et continuer à l’étape suivante.  
  
##  <a name="vcconattachnewviewa3"></a> Créer et attacher la nouvelle vue  
 Pour créer et attacher la nouvelle vue, vous devez modifier le `InitInstance` fonction de votre classe d’application. La modification ajoute le nouveau code qui crée un nouvel objet de vue, puis initialise les deux `m_pOldView` et `m_pNewView` avec les deux objets de vue existante.  
  
 Étant donné que la nouvelle vue est créée dans le `InitInstance` (fonction), les vues nouvelles et existantes rendre persistantes pour la durée de vie de l’application. Toutefois, l’application peut créer tout aussi facilement dynamiquement la nouvelle vue.  
  
 Insérez ce code après l’appel à `ProcessShellCommand`:  
  
 [!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]  
  
 Enregistrez vos modifications et continuer à l’étape suivante.  
  
##  <a name="vcconswitchingfunctiona4"></a> Implémenter la fonction d’échange  
 Dans l’étape précédente, vous avez ajouté le code qui a créé et initialisé un nouvel objet de vue. La dernière étape importante consiste à implémenter la méthode de commutation, `SwitchView`.  
  
 À la fin du fichier d’implémentation pour votre classe d’application (*MYWINAPP. CPP*), ajoutez la définition de méthode suivante :  
  
 [!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]  
  
 Enregistrez vos modifications et continuer à l’étape suivante.  
  
##  <a name="vcconswitchingtheviewa5"></a> Ajouter la prise en charge pour le basculement de la vue  
 La dernière étape consiste à ajouter du code qui appelle la `SwitchView` méthode lorsque l’application a besoin basculer entre les vues. Cela est possible de plusieurs façons : en ajoutant un nouvel élément de menu pour l’utilisateur de choisir ou échange interne des vues lorsque certaines conditions sont remplies.  
  
 Pour plus d’informations sur l’ajout de nouveaux éléments de menu et les fonctions gestionnaires de commandes, consultez [gestionnaires pour les commandes et les Notifications de contrôle](../mfc/handlers-for-commands-and-control-notifications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture document/vue](../mfc/document-view-architecture.md)

