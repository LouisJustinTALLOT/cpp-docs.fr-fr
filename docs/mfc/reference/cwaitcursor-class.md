---
description: 'En savoir plus sur : classe CWaitCursor'
title: CWaitCursor, classe
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 5d2323e3be78154c6a9d3ded55ab9e1a951d78b7
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951492"
---
# <a name="cwaitcursor-class"></a>CWaitCursor, classe

Permet en une ligne d'afficher un curseur d'attente, généralement sous forme de sablier, pendant que vous effectuez une longue opération.

## <a name="syntax"></a>Syntaxe

```
class CWaitCursor
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Construit un `CWaitCursor` objet et affiche le curseur d’attente.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CWaitCursor :: Restore](#restore)|Restaure le curseur d’attente après qu’il a été modifié.|

## <a name="remarks"></a>Remarques

`CWaitCursor` n’a pas de classe de base.

Pour de bonnes pratiques de programmation Windows, vous devez afficher un curseur d’attente chaque fois que vous effectuez une opération qui prend un certain temps.

Pour afficher un curseur d’attente, il vous suffit de définir une `CWaitCursor` variable avant le code qui effectue l’opération de longue durée. Le constructeur de l’objet provoque l’affichage automatique du curseur d’attente.

Lorsque l’objet est hors de portée (à la fin du bloc dans lequel l' `CWaitCursor` objet est déclaré), son destructeur définit le curseur sur le curseur précédent. En d’autres termes, l’objet effectue automatiquement le nettoyage nécessaire.

> [!NOTE]
> En raison de la façon dont leurs constructeurs et leurs destructeurs fonctionnent, les `CWaitCursor` objets sont toujours déclarés en tant que variables locales ; ils ne sont jamais déclarés en tant que variables globales et ne sont pas alloués avec **`new`** .

Si vous effectuez une opération qui peut entraîner la modification du curseur, par exemple l’affichage d’une boîte de message ou d’une boîte de dialogue, appelez la fonction membre [Restore](#restore) pour restaurer le curseur d’attente. Il est possible d’appeler `Restore` même lorsqu’un curseur d’attente est actuellement affiché.

Une autre façon d’afficher un curseur d’attente consiste à utiliser la combinaison de [CCmdTarget :: BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget :: EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)et peut-être [CCmdTarget :: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Toutefois, `CWaitCursor` est plus facile à utiliser, car vous n’avez pas besoin de définir le curseur sur le curseur précédent lorsque vous avez terminé l’opération de longue durée.

> [!NOTE]
> MFC définit et restaure le curseur à l’aide de la fonction virtuelle [CWinApp ::D owaitcursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) . Vous pouvez remplacer cette fonction pour fournir un comportement personnalisé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CWaitCursor`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a> CWaitCursor::CWaitCursor

Pour afficher un curseur d’attente, il vous suffit de déclarer un `CWaitCursor` objet avant le code qui effectue l’opération de longue durée.

```
CWaitCursor();
```

### <a name="remarks"></a>Remarques

Le constructeur provoque automatiquement l’affichage du curseur d’attente.

Lorsque l’objet est hors de portée (à la fin du bloc dans lequel l' `CWaitCursor` objet est déclaré), son destructeur définit le curseur sur le curseur précédent. En d’autres termes, l’objet effectue automatiquement le nettoyage nécessaire.

Vous pouvez tirer parti du fait que le destructeur est appelé à la fin du bloc (qui peut être avant la fin de la fonction) pour rendre le curseur d’attente actif dans une partie seulement de votre fonction. Cette technique est illustrée dans le deuxième exemple ci-dessous.

> [!NOTE]
> En raison du mode de fonctionnement de leurs constructeurs et destructeurs, les `CWaitCursor` objets sont toujours déclarés en tant que variables locales. ils ne sont jamais déclarés en tant que variables globales et ne sont pas alloués avec **`new`** .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a> CWaitCursor :: Restore

Pour restaurer le curseur d’attente, appelez cette fonction après avoir effectué une opération, telle que l’affichage d’une boîte de message ou d’une boîte de dialogue, qui peut remplacer le curseur d’attente par un autre curseur.

```cpp
void Restore();
```

### <a name="remarks"></a>Remarques

Vous pouvez appeler `Restore` même lorsque le curseur d’attente est actuellement affiché.

Si vous devez restaurer le curseur d’attente dans une fonction différente de celle dans laquelle l' `CWaitCursor` objet est déclaré, vous pouvez appeler [CCmdTarget :: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget :: BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget :: EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget :: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp ::D oWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Modifier le pointeur de la souris pour une fenêtre dans MFC à l’aide de Visual C++](/troubleshoot/cpp/change-mouse-pointer-window-mfc)
