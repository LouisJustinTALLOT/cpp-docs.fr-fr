---
title: Spécification de niveaux de fonctionnalité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f32b9502d2e8bd1c1483d817b759ca204f5c9c1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381145"
---
# <a name="specifying-levels-of-functionality"></a>Spécification de niveaux de fonctionnalité
Cet article décrit comment ajouter des niveaux suivants de fonctionnalités à votre [CObject](../mfc/reference/cobject-class.md)-classe dérivée :  
  
-   [Informations de classe d’exécution](#_core_to_add_run.2d.time_class_information)  
  
-   [Prise en charge la création dynamique](#_core_to_add_dynamic_creation_support)  
  
-   [Prise en charge de la sérialisation](#_core_to_add_serialization_support)  
  
 Pour obtenir une description générale de `CObject` des fonctionnalités, consultez l’article [dérivant une classe de CObject](../mfc/deriving-a-class-from-cobject.md).  
  
-   [Informations de classe d’exécution](#_core_to_add_run.2d.time_class_information)  
#### <a name="_core_to_add_run.2d.time_class_information"></a> Pour ajouter des informations de classe d’exécution  
  
1.  Dérivez votre classe de `CObject`, comme décrit dans la [dérivant une classe de CObject](../mfc/deriving-a-class-from-cobject.md) l’article.  
  
2.  Utilisez le `DECLARE_DYNAMIC` macro dans votre déclaration de classe, comme indiqué ici :  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]  
  
3.  Utilisez le `IMPLEMENT_DYNAMIC` macro dans le fichier d’implémentation (. CPP) de votre classe. Cette macro prend comme arguments le nom de la classe et de sa classe de base, comme suit :  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  Placez toujours `IMPLEMENT_DYNAMIC` dans le fichier d’implémentation (. CPP) pour votre classe. Le `IMPLEMENT_DYNAMIC` macro doit être évaluée une seule fois pendant une compilation et ne doit donc pas être utilisé dans un fichier d’interface (. H) qui pourrait potentiellement être inclus dans plusieurs fichiers.  
  
#### <a name="_core_to_add_dynamic_creation_support"></a> Pour ajouter la prise en charge la création dynamique  
  
1.  Dérivez votre classe de `CObject`.  
  
2.  Utilisez le `DECLARE_DYNCREATE` macro dans la déclaration de classe.  
  
3.  Définissez un constructeur sans argument (constructeur par défaut).  
  
4.  Utilisez le `IMPLEMENT_DYNCREATE` macro dans le fichier d’implémentation de classe.  
  
#### <a name="_core_to_add_serialization_support"></a> Pour ajouter la prise en charge de la sérialisation  
  
1.  Dérivez votre classe de `CObject`.  
  
2.  Remplacer la `Serialize` fonction membre.  
  
    > [!NOTE]
    >  Si vous appelez `Serialize` directement, autrement dit, vous ne souhaitez pas sérialiser l’objet via un pointeur polymorphe, ignorez les étapes 3 à 5.  
  
3.  Utilisez le `DECLARE_SERIAL` macro dans la déclaration de classe.  
  
4.  Définissez un constructeur sans argument (constructeur par défaut).  
  
5.  Utilisez le `IMPLEMENT_SERIAL` macro dans le fichier d’implémentation de classe.  
  
> [!NOTE]
>  Un « pointeur polymorphe » pointe vers un objet d’une classe (l’appeler A) ou un objet de toute classe dérivée d’un (par exemple, B). Pour sérialiser via un pointeur polymorphe, la structure doit déterminer la classe d’exécution de l’objet, qu'il sérialise (B), dans la mesure où il peut être un objet de toute classe dérivée à partir d’une classe de base (A).  
  
 Pour plus d’informations sur la façon d’activer la sérialisation lorsque vous dérivez votre classe de `CObject`, consultez les articles [fichiers dans MFC](../mfc/files-in-mfc.md) et [sérialisation](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dérivation d’une classe de CObject](../mfc/deriving-a-class-from-cobject.md)
