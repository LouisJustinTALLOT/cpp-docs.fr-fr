---
title: CPtrList, classe
ms.date: 11/04/2016
f1_keywords:
- CPtrList
helpviewer_keywords:
- lists, generic
- CPtrList class [MFC]
- generic lists
ms.assetid: 4139a09c-4338-4f42-9eea-51336120b43c
ms.openlocfilehash: 5b88b0950b3b46f9738bd26080883c00d46f8555
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266235"
---
# <a name="cptrlist-class"></a>CPtrList, classe

Prend en charge des listes de pointeurs void.

## <a name="syntax"></a>Syntaxe

```
class CPtrList : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CPtrList` sont similaires aux fonctions membres de classe [CObList](../../mfc/reference/coblist-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObList` pour connaître les spécificités des fonctions membres. Partout où vous voyez un `CObject` pointeur en tant que paramètre de fonction ou valeur de retour, remplacez par un pointeur vers **void**.

`CObject*& CObList::GetHead() const;`

par exemple, se traduit par

`void*& CPtrList::GetHead() const;`

## <a name="remarks"></a>Notes

`CPtrList` incorpore la macro IMPLEMENT_DYNAMIC pour prendre en charge d’accès de type au moment de l’exécution et le vidage à un `CDumpContext` objet. Si vous avez besoin d’un vidage d’éléments de liste individuels de pointeur, vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.

Listes de pointeur ne peut pas être sérialisés.

Quand un `CPtrList` objet est supprimé, ou lorsque ses éléments sont supprimés, seuls les pointeurs sont supprimées, pas les entités qu’elles référencent.

Pour plus d’informations sur l’utilisation de `CPtrList`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CPtrList`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcoll.h

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CObList, classe](../../mfc/reference/coblist-class.md)
