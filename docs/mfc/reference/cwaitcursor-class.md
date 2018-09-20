---
title: Cwaitcursor, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs:
- C++
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5b7deaf83c093c16b30ee04d8c5924c1d567d86c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435803"
---
# <a name="cwaitcursor-class"></a>Cwaitcursor, classe

Permet en une ligne d'afficher un curseur d'attente, généralement sous forme de sablier, pendant que vous effectuez une longue opération.

## <a name="syntax"></a>Syntaxe

```
class CWaitCursor
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Construit un `CWaitCursor` de l’objet et affiche le curseur d’attente.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWaitCursor::Restore](#restore)|Restaure le curseur d’attente après sa modification.|

## <a name="remarks"></a>Notes

`CWaitCursor` n’a pas d’une classe de base.

Windows de bonnes pratiques de programmation nécessitent que vous afficher un curseur d’attente chaque fois que vous effectuez une opération qui prend un certain temps.

Pour afficher un curseur d’attente, définissez simplement un `CWaitCursor` variable avant le code qui effectue l’opération de longue durée. Constructeur de l’objet entraîne automatiquement le curseur d’attente à afficher.

Lorsque l’objet est hors de portée (à la fin du bloc dans lequel le `CWaitCursor` objet est déclaré), son destructeur définit le curseur jusqu’au curseur précédente. En d’autres termes, l’objet effectue automatiquement le nettoyage nécessaire.

> [!NOTE]
>  En raison de leurs constructeurs et les destructeurs fonctionnement, `CWaitCursor` objets sont toujours déclarés en tant que variables locales, elles ne sont jamais déclarées comme des variables globales ni alloués avec **nouveau**.

Si vous effectuez une opération qui peut entraîner le curseur à modifier, comme l’affichage d’une boîte de message ou la boîte de dialogue, l’appel de la [restaurer](#restore) fonction membre pour restaurer le curseur d’attente. Il est OK appeler `Restore` même lorsqu’un curseur d’attente est actuellement affiché.

Une autre façon d’afficher un curseur d’attente consiste à utiliser la combinaison de [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)et, éventuellement, [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Toutefois, `CWaitCursor` est plus facile à utiliser, car vous n’avez pas besoin de définir le curseur jusqu’au curseur précédente lorsque vous avez terminé avec l’opération longue.

> [!NOTE]
>  MFC définit et restaure le curseur à l’aide de la [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) fonction virtuelle. Vous pouvez remplacer cette fonction pour fournir un comportement personnalisé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CWaitCursor`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

##  <a name="cwaitcursor"></a>  CWaitCursor::CWaitCursor

Pour afficher un curseur d’attente, déclarez un `CWaitCursor` objet avant le code qui effectue l’opération longue.

```
CWaitCursor();
```

### <a name="remarks"></a>Notes

Le constructeur entraîne automatiquement le curseur d’attente à afficher.

Lorsque l’objet est hors de portée (à la fin du bloc dans lequel le `CWaitCursor` objet est déclaré), son destructeur définit le curseur jusqu’au curseur précédente. En d’autres termes, l’objet effectue automatiquement le nettoyage nécessaire.

Vous pouvez tirer parti du fait que le destructeur est appelé à la fin du bloc (qui peut être avant la fin de la fonction) pour que le curseur d’attente active qu’une partie de votre fonction. Cette technique est illustrée dans le deuxième exemple ci-dessous.

> [!NOTE]
>  En raison de leurs constructeurs et les destructeurs fonctionnement, `CWaitCursor` objets sont toujours déclarés en tant que variables locales, elles ne sont jamais déclarées comme des variables globales, ni si elles sont allouées avec **nouveau**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

##  <a name="restore"></a>  CWaitCursor::Restore

Pour restaurer le curseur d’attente, appelez cette fonction après une opération, comme l’affichage d’une boîte de message ou de la boîte de dialogue, qui peut changer le curseur d’attente à un autre curseur.

```
void Restore();
```

### <a name="remarks"></a>Notes

Il s’agit de OK à appeler `Restore` même lorsque le curseur d’attente est actuellement affiché.

Si vous devez restaurer le curseur d’attente tandis que dans une fonction différente de celle dans laquelle le `CWaitCursor` objet est déclaré, vous pouvez appeler [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Comment faire : modifier le curseur de souris dans une Application de classe Microsoft Foundation](http://go.microsoft.com/fwlink/p/?linkid=128044)



