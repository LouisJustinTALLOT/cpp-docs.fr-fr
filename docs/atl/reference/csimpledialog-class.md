---
title: Classe CSimpleDialog
ms.date: 11/04/2016
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
ms.openlocfilehash: 345372d71ad96a74bb0ae6dd7e89bdf0724cd822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330825"
---
# <a name="csimpledialog-class"></a>Classe CSimpleDialog

Cette classe met en œuvre une boîte de dialogue modal de base.

## <a name="syntax"></a>Syntaxe

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>Paramètres

*t_wDlgTemplateID*

L’ID de ressource de la ressource de modèle de dialogue.

*t_bCenter*<br/>
VRAI si l’objet de dialogue doit être centré sur la fenêtre du propriétaire; autrement FALSE.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleDialog::DoModal](#domodal)|Crée une boîte de dialogue modal.|

## <a name="remarks"></a>Notes

Implémente une boîte de dialogue modal avec fonctionnalité de base. `CSimpleDialog`fournit une prise en charge pour les contrôles communs Windows seulement. Pour créer et afficher une boîte de dialogue modal, créez un exemple de cette classe, en fournissant le nom d’un modèle de ressources existant pour la boîte de dialogue. L’objet de la boîte de dialogue se ferme lorsque l’utilisateur clique sur n’importe quel contrôle avec une valeur prédéfini (comme IDOK ou IDCANCEL).

`CSimpleDialog`vous permet de créer uniquement des boîtes de dialogue modal. `CSimpleDialog`fournit la procédure de boîte de dialogue, qui utilise la carte de message par défaut pour diriger les messages vers les gestionnaires appropriés.

Voir [la mise en œuvre d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md) pour plus d’informations.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** atlwin.h

## <a name="csimpledialogdomodal"></a><a name="domodal"></a>CSimpleDialog::DoModal

Invoque une boîte de dialogue modal et renvoie le résultat de la boîte de dialogue une fois terminé.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Une poignée pour le parent de la boîte de dialogue. Si aucune valeur n’est fournie, le parent est réglé à la fenêtre active actuelle.

### <a name="return-value"></a>Valeur de retour

En cas de succès, la valeur de retour est l’ID de ressource du contrôle qui a rejeté la boîte de dialogue.

Si la fonction échoue, la valeur de rendement est de -1. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

### <a name="remarks"></a>Notes

Cette méthode gère toute interaction avec l’utilisateur pendant que la boîte de dialogue est active. C’est ce qui rend la boîte de dialogue modale; c’est-à-dire que l’utilisateur ne peut pas interagir avec d’autres fenêtres jusqu’à ce que la boîte de dialogue soit fermée.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
