---
description: 'En savoir plus sur : classe CSimpleDialog'
title: CSimpleDialog, classe
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
ms.openlocfilehash: 50889c4387515c85cd3c6e53bf12e7c0494504ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140645"
---
# <a name="csimpledialog-class"></a>CSimpleDialog, classe

Cette classe implémente une boîte de dialogue modale de base.

## <a name="syntax"></a>Syntaxe

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>Paramètres

*t_wDlgTemplateID*

ID de ressource de la ressource de modèle de boîte de dialogue.

*t_bCenter*<br/>
TRUE si l’objet Dialog doit être centré sur la fenêtre propriétaire ; Sinon, FALSe.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSimpleDialog ::D oModal](#domodal)|Crée une boîte de dialogue modale.|

## <a name="remarks"></a>Notes

Implémente une boîte de dialogue modale avec des fonctionnalités de base. `CSimpleDialog` prend uniquement en charge les contrôles communs Windows. Pour créer et afficher une boîte de dialogue modale, créez une instance de cette classe, en fournissant le nom d’un modèle de ressource existant pour la boîte de dialogue. L’objet de boîte de dialogue se ferme quand l’utilisateur clique sur un contrôle avec une valeur prédéfinie (par exemple, IDOK ou IDCANCEL).

`CSimpleDialog` vous permet de créer uniquement des boîtes de dialogue modales. `CSimpleDialog` fournit la procédure de boîte de dialogue, qui utilise la table des messages par défaut pour diriger les messages vers les gestionnaires appropriés.

Pour plus d’informations, consultez [implémentation d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** atlwin. h

## <a name="csimpledialogdomodal"></a><a name="domodal"></a> CSimpleDialog ::D oModal

Appelle une boîte de dialogue modale et retourne le résultat de la boîte de dialogue lorsque vous avez terminé.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Paramètres

*hWndParent*<br/>
Handle du parent de la boîte de dialogue. Si aucune valeur n’est fournie, le parent est défini sur la fenêtre active actuelle.

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, la valeur de retour est l’ID de ressource du contrôle qui a ignoré la boîte de dialogue.

Si la fonction échoue, la valeur de retour est-1. Pour obtenir des informations plus complètes sur les erreurs, appelez `GetLastError`.

### <a name="remarks"></a>Notes

Cette méthode gère toutes les interactions avec l’utilisateur pendant que la boîte de dialogue est active. C’est ce qui rend la boîte de dialogue modale ; autrement dit, l’utilisateur ne peut pas interagir avec d’autres fenêtres tant que la boîte de dialogue n’est pas fermée.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
