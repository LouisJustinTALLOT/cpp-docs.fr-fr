---
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
ms.openlocfilehash: 48ef8f9c965f54deafcc62451639f8c31021e900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373176"
---
# <a name="cwaitcursor-class"></a>CWaitCursor, classe

Permet en une ligne d'afficher un curseur d'attente, généralement sous forme de sablier, pendant que vous effectuez une longue opération.

## <a name="syntax"></a>Syntaxe

```
class CWaitCursor
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Construit un `CWaitCursor` objet et affiche le curseur d’attente.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWaitCursor::Restaurer](#restore)|Restaure le curseur d’attente après qu’il a été changé.|

## <a name="remarks"></a>Notes

`CWaitCursor`n’a pas de classe de base.

Les bonnes pratiques de programmation Windows exigent que vous affichez un curseur d’attente chaque fois que vous effectuez une opération qui prend une quantité notable de temps.

Pour afficher un curseur d’attente, il suffit de définir une `CWaitCursor` variable avant le code qui effectue la longue opération. Le constructeur de l’objet provoque automatiquement l’affichage du curseur d’attente.

Lorsque l’objet sort de portée (à la `CWaitCursor` fin du bloc dans lequel l’objet est déclaré), son destructeur fixe le curseur au curseur précédent. En d’autres termes, l’objet effectue automatiquement le nettoyage nécessaire.

> [!NOTE]
> En raison du fonctionnement de leurs `CWaitCursor` constructeurs et destructeurs, les objets sont toujours déclarés comme des variables locales — ils ne sont jamais déclarés comme variables globales et ne sont pas attribués avec **de nouvelles**.

Si vous effectuez une opération qui pourrait faire changer le curseur, comme l’affichage d’une boîte de message ou d’une boîte de dialogue, appelez la fonction du membre [Restaurer](#restore) pour restaurer le curseur d’attente. Il est acceptable `Restore` d’appeler même lorsqu’un curseur d’attente est actuellement affiché.

Une autre façon d’afficher un curseur d’attente est d’utiliser la combinaison de [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor), et peut-être [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Cependant, `CWaitCursor` est plus facile à utiliser parce que vous n’avez pas besoin de régler le curseur au curseur précédent lorsque vous avez terminé avec la longue opération.

> [!NOTE]
> MFC définit et restaure le curseur à l’aide de la fonction virtuelle [CWinApp::DoWaitCursor.](../../mfc/reference/cwinapp-class.md#dowaitcursor) Vous pouvez remplacer cette fonction pour fournir un comportement personnalisé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CWaitCursor`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor::CWaitCursor

Pour afficher un curseur d’attente, il suffit de déclarer un `CWaitCursor` objet avant le code qui effectue la longue opération.

```
CWaitCursor();
```

### <a name="remarks"></a>Notes

Le constructeur provoque automatiquement l’affichage du curseur d’attente.

Lorsque l’objet sort de portée (à la `CWaitCursor` fin du bloc dans lequel l’objet est déclaré), son destructeur fixe le curseur au curseur précédent. En d’autres termes, l’objet effectue automatiquement le nettoyage nécessaire.

Vous pouvez profiter du fait que le destructeur est appelé à la fin du bloc (qui pourrait être avant la fin de la fonction) pour rendre le curseur d’attente actif dans seulement une partie de votre fonction. Cette technique est montrée dans le deuxième exemple ci-dessous.

> [!NOTE]
> En raison du fonctionnement de leurs `CWaitCursor` constructeurs et destructeurs, les objets sont toujours déclarés comme des variables locales — ils ne sont jamais déclarés comme variables globales, et ils ne sont pas attribués avec **de nouvelles**.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor::Restaurer

Pour restaurer le curseur d’attente, appelez cette fonction après l’exécution d’une opération, comme l’affichage d’une boîte de message ou d’une boîte de dialogue, qui pourrait changer le curseur d’attente à un autre curseur.

```
void Restore();
```

### <a name="remarks"></a>Notes

Il est acceptable `Restore` d’appeler même lorsque le curseur d’attente est actuellement affiché.

Si vous avez besoin de restaurer le curseur d’attente `CWaitCursor` tandis que dans une fonction autre que celle dans laquelle l’objet est déclaré, vous pouvez appeler [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Comment puis-je: Changer le curseur de souris dans une application de classe Microsoft Foundation](https://go.microsoft.com/fwlink/p/?linkid=128044)
