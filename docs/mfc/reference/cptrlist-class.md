---
description: 'En savoir plus sur : classe CPtrList'
title: CPtrList, classe
ms.date: 11/04/2016
f1_keywords:
- CPtrList
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
ms.openlocfilehash: 27849db4687860ab68feb548de1ed8ad209b73a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343249"
---
# <a name="cptrlist-class"></a>CPtrList, classe

Prend en charge des listes de pointeurs void.

## <a name="syntax"></a>Syntaxe

```
class CPtrList : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CPtrList` sont similaires aux fonctions membres de la classe [CObList](../../mfc/reference/coblist-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObList` pour connaître les spécificités des fonctions membres. Partout où vous voyez un `CObject` pointeur sous la forme d’un paramètre de fonction ou d’une valeur de retour, remplacez un pointeur par **`void`** .

`CObject*& CObList::GetHead() const;`

par exemple, se traduit par

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>Notes

`CPtrList` incorpore la macro IMPLEMENT_DYNAMIC pour prendre en charge l’accès aux types au moment de l’exécution et le vidage sur un `CDumpContext` objet. Si vous avez besoin d’un vidage d’éléments de liste de pointeurs individuels, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Les listes de pointeurs ne peuvent pas être sérialisées.

Lorsqu’un `CPtrList` objet est supprimé ou que ses éléments sont supprimés, seuls les pointeurs sont supprimés, et non les entités auxquelles ils font référence.

Pour plus d’informations sur l’utilisation de `CPtrList` , consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll. h

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObList (classe)](../../mfc/reference/coblist-class.md)
