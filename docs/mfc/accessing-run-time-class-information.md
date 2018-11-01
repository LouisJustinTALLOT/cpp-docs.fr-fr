---
title: Accès aux informations de classe d'exécution
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: 061cc04857b0d1763fb4ee975912bcca1b9d014f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455274"
---
# <a name="accessing-run-time-class-information"></a>Accès aux informations de classe d'exécution

Cet article explique comment accéder aux informations sur la classe d'un objet au moment de l'exécution.

> [!NOTE]
>  MFC n’utilise pas le [Run-Time Type Information](../cpp/run-time-type-information.md) support (RTTI) introduite dans Visual C++ 4.0.

Si vous avez dérivé votre classe de [CObject](../mfc/reference/cobject-class.md) et utilisé la **DECLARE**_**dynamique** et `IMPLEMENT_DYNAMIC`, le `DECLARE_DYNCREATE` et `IMPLEMENT_DYNCREATE`, ou le `DECLARE_SERIAL` et `IMPLEMENT_SERIAL` macros expliqué dans l’article [dérivant une classe de CObject](../mfc/deriving-a-class-from-cobject.md), la `CObject` classe a la possibilité de déterminer la classe exacte d’un objet au moment de l’exécution.

Cette option est très pratique lorsqu’une vérification de type supplémentaire des arguments de fonction est nécessaire et lorsque vous devez écrire un code spécial en fonction de la classe d’un autre objet. Toutefois, cette pratique n'est généralement pas recommandée car elle duplique les fonctionnalités des fonctions virtuelles.

La fonction membre `CObject` `IsKindOf` peut permettre de déterminer si un objet particulier appartient à une classe spécifiée ou si elle est dérivée d'une classe spécifique. L'argument pour `IsKindOf` est un objet `CRuntimeClass` que vous pouvez obtenir à l'aide de la macro `RUNTIME_CLASS` avec le nom de la classe.

### <a name="to-use-the-runtimeclass-macro"></a>Pour utiliser la macro RUNTIME_CLASS

1. Utilisez `RUNTIME_CLASS` avec le nom de la classe, comme indiqué ici pour la classe `CObject` :

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Vous devrez rarement accéder à l'objet de classe d'exécution directement. Un usage plus courant consiste à passer l'objet de classe d'exécution à la fonction `IsKindOf`, comme le montre la procédure suivante. La fonction `IsKindOf` teste un objet pour voir s'il appartient à une classe donnée.

#### <a name="to-use-the-iskindof-function"></a>Pour utiliser la fonction IsKindOf

1. Vérifiez que la classe possède la prise en charge de la classe d'exécution. Autrement dit, la classe doit avoir été dérivée directement ou indirectement de `CObject` et utilisé la **DECLARE**_**dynamique** et `IMPLEMENT_DYNAMIC`, le `DECLARE_DYNCREATE` et `IMPLEMENT_DYNCREATE`, ou le `DECLARE_SERIAL` et `IMPLEMENT_SERIAL` macros expliqué dans l’article [dérivant une classe de CObject](../mfc/deriving-a-class-from-cobject.md).

1. Appelez la méthode `IsKindOf` pour les objets de cette classe, à l’aide de la macro `RUNTIME_CLASS` pour générer l’argument `CRuntimeClass`, comme indiqué ici :

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf retourne **TRUE** si l’objet est un membre de la classe spécifiée ou d’une classe dérivée de la classe spécifiée. `IsKindOf` ne prend pas en charge l'héritage multiple ou les classes de base virtuelles, bien que vous puissiez utiliser l'héritage multiple pour vos classes dérivées Microsoft Foundation, si nécessaire.

Une utilisation des informations sur la classe d'exécution est en création dynamique des objets. Cette procédure est décrite dans l’article [création d’objets dynamiques](../mfc/dynamic-object-creation.md).

Pour plus d’informations sur la sérialisation et les informations de classe d’exécution, consultez les articles [fichiers dans MFC](../mfc/files-in-mfc.md) et [sérialisation](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CObject](../mfc/using-cobject.md)

