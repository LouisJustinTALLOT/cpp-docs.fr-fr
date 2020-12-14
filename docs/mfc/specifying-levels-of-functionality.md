---
description: 'En savoir plus sur : spécification des niveaux de fonctionnalité'
title: Spécification de niveaux de fonctionnalité
ms.date: 11/06/2018
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
ms.openlocfilehash: 1b016cd5a41d3e09790f678a2d49d88df33d9782
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216845"
---
# <a name="specifying-levels-of-functionality"></a>Spécification de niveaux de fonctionnalité

Cet article explique comment ajouter les niveaux de fonctionnalité suivants à votre classe dérivée de [CObject](../mfc/reference/cobject-class.md):

- Informations de classe au moment de l’exécution

- Prise en charge de la création dynamique

- Prise en charge de la sérialisation

Pour obtenir une description générale des `CObject` fonctionnalités, consultez l’article [dérivation d’une classe à partir de CObject](../mfc/deriving-a-class-from-cobject.md).

## <a name="to-add-run-time-class-information"></a>Pour ajouter des informations de classe au moment de l’exécution

1. Dérivez votre classe de `CObject` , comme décrit dans l’article [dériver une classe de CObject](../mfc/deriving-a-class-from-cobject.md) .

1. Utilisez la macro DECLARE_DYNAMIC dans votre déclaration de classe, comme illustré ici :

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. Utilisez la macro IMPLEMENT_DYNAMIC dans le fichier d’implémentation (. CPP) de votre classe. Cette macro prend comme arguments le nom de la classe et de sa classe de base, comme suit :

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
> Placez toujours IMPLEMENT_DYNAMIC dans le fichier d’implémentation (. CPP) pour votre classe. La macro IMPLEMENT_DYNAMIC ne doit être évaluée qu’une seule fois pendant une compilation et ne doit donc pas être utilisée dans un fichier d’interface (. H) qui pourrait éventuellement être inclus dans plusieurs fichiers.

## <a name="to-add-dynamic-creation-support"></a>Pour ajouter la prise en charge de la création dynamique

1. Dérivez votre classe de `CObject` .

1. Utilisez la macro DECLARE_DYNCREATE dans la déclaration de classe.

1. Définissez un constructeur sans argument (constructeur par défaut).

1. Utilisez la macro IMPLEMENT_DYNCREATE dans le fichier d’implémentation de classe.

## <a name="to-add-serialization-support"></a>Pour ajouter la prise en charge de la sérialisation

1. Dérivez votre classe de `CObject` .

1. Substituez la `Serialize` fonction membre.

   > [!NOTE]
   > Si vous appelez `Serialize` directement, autrement dit, si vous ne souhaitez pas sérialiser l’objet à l’aide d’un pointeur polymorphe, omettez les étapes 3 à 5.

1. Utilisez la macro DECLARE_SERIAL dans la déclaration de classe.

1. Définissez un constructeur sans argument (constructeur par défaut).

1. Utilisez la macro IMPLEMENT_SERIAL dans le fichier d’implémentation de classe.

> [!NOTE]
> Un « pointeur polymorphe » pointe sur un objet d’une classe (appelez-le A) ou sur un objet de toute classe dérivée d’un (par exemple, B). Pour sérialiser via un pointeur polymorphe, le Framework doit déterminer la classe Runtime de l’objet qu’il sérialise (B), car il peut s’agir d’un objet de toute classe dérivée d’une classe de base (A).

Pour plus d’informations sur l’activation de la sérialisation lorsque vous dérivez votre classe de `CObject` , consultez les articles [fichiers dans MFC](../mfc/files-in-mfc.md) et [sérialisation](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Dérivation d’une classe de CObject](../mfc/deriving-a-class-from-cobject.md)
