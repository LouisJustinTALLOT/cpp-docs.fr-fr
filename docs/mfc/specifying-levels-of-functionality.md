---
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
ms.openlocfilehash: c3b4ecb38054748f36d75ca43e32d6447d3d2428
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307287"
---
# <a name="specifying-levels-of-functionality"></a>Spécification de niveaux de fonctionnalité

Cet article décrit comment ajouter les niveaux suivants de fonctionnalités à votre [CObject](../mfc/reference/cobject-class.md)-classe dérivée :

- Informations de classe d’exécution

- Prise en charge la création dynamique

- Prise en charge de la sérialisation

Pour obtenir une description générale de `CObject` fonctionnalités, consultez l’article [dérivant une classe de CObject](../mfc/deriving-a-class-from-cobject.md).

## <a name="to-add-run-time-class-information"></a>Pour ajouter des informations de classe d’exécution

1. Dérivez votre classe de `CObject`, comme décrit dans la [dérivant une classe de CObject](../mfc/deriving-a-class-from-cobject.md) article.

1. Utilisez la macro DECLARE_DYNAMIC dans votre déclaration de classe, comme illustré ici :

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. Utilisez la macro IMPLEMENT_DYNAMIC dans le fichier d’implémentation (. (CPP) de votre classe. Cette macro prend comme arguments le nom de la classe et de sa classe de base, comme suit :

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
> Placez toujours IMPLEMENT_DYNAMIC dans le fichier d’implémentation (. (CPP) pour votre classe. La macro IMPLEMENT_DYNAMIC doit être évaluée une seule fois durant une compilation et ne doit donc pas être utilisée dans un fichier d’interface (. (H) qui pourrait potentiellement être inclus dans plusieurs fichiers.

## <a name="to-add-dynamic-creation-support"></a>Pour ajouter la prise en charge la création dynamique

1. Dérivez votre classe de `CObject`.

1. Utilisez la macro DECLARE_DYNCREATE dans la déclaration de classe.

1. Définir un constructeur sans arguments (un constructeur par défaut).

1. Utilisez la macro IMPLEMENT_DYNCREATE dans le fichier d’implémentation de classe.

## <a name="to-add-serialization-support"></a>Pour ajouter la prise en charge de la sérialisation

1. Dérivez votre classe de `CObject`.

1. Remplacer le `Serialize` fonction membre.

   > [!NOTE]
   > Si vous appelez `Serialize` directement, autrement dit, vous ne souhaitez pas sérialiser l’objet via un pointeur polymorphe, ignorez les étapes 3 à 5.

1. Utilisez la macro DECLARE_SERIAL dans la déclaration de classe.

1. Définir un constructeur sans arguments (un constructeur par défaut).

1. Utilisez la macro IMPLEMENT_SERIAL dans le fichier d’implémentation de classe.

> [!NOTE]
> Un « pointeur polymorphe » pointe vers un objet d’une classe (appelez-le A) ou à un objet de n’importe quelle classe dérivée d’un (par exemple, B). Pour sérialiser via un pointeur polymorphe, la structure doit déterminer la classe d’exécution de l’objet, qu'il sérialise (B), dans la mesure où il peut être un objet de n’importe quelle classe dérivée à partir d’une classe de base (A).

Pour plus d’informations sur la façon d’activer la sérialisation lorsque vous dérivez votre classe de `CObject`, consultez les articles [fichiers dans MFC](../mfc/files-in-mfc.md) et [sérialisation](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Dérivation d’une classe de CObject](../mfc/deriving-a-class-from-cobject.md)
