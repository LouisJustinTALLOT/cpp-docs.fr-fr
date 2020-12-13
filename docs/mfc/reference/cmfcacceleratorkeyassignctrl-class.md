---
description: 'En savoir plus sur : classe Cmfcacceleratorkeyassignctrl,'
title: CMFCAcceleratorKeyAssignCtrl, classe
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: 0f5584dfa521f45841691bff3775d9cd98808b9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336594"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl, classe

La `CMFCAcceleratorKeyAssignCtrl` classe étend la [classe CEdit](../../mfc/reference/cedit-class.md) pour prendre en charge des boutons système supplémentaires tels que ALT, Ctrl et Maj.

## <a name="syntax"></a>Syntaxe

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Construit un objet `CMFCAcceleratorKeyAssignCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Récupère la structure `ACCEL` pour une touche de raccourci enfoncée dans l'objet `CMFCAcceleratorKeyAssignCtrl`.|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Détermine si une touche de raccourci a été définie.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour traduire les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Réinitialise la touche de raccourci.|

## <a name="remarks"></a>Notes

Cette classe étend les fonctionnalités de la classe `CEdit` en prenant en charge les touches de raccourci, aussi appelées touches accélérateur. La `CMFCAcceleratorKeyAssignCtrl` classe fonctionne comme une [classe CEdit](../../mfc/reference/cedit-class.md) et peut également reconnaître les boutons système.

Cette classe mappe les combinaisons de touches de raccourci physiques à des valeurs de chaîne. Par exemple, supposons que la combinaison de touches Alt+B est mappé à la chaîne « Alt+B ». Quand l'utilisateur appuie sur cette combinaison de touches dans un objet `CMFCAcceleratorKeyAssignCtrl`, « Alt+B » est présenté à l'utilisateur. Pour plus d’informations sur le mappage entre les touches de raccourci et un format de chaîne, consultez [cmfcacceleratorkey,, classe](../../mfc/reference/cmfcacceleratorkey-class.md).

## <a name="example"></a>Exemple

L'exemple suivant montre comment construire un objet `CMFCAcceleratorKeyAssignCtrl` et utiliser sa méthode `ResetKey` pour réinitialiser la touche de raccourci.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxacceleratorkeyassignctrl. h

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a> Cmfcacceleratorkeyassignctrl, :: Cmfcacceleratorkeyassignctrl,

Construit un objet [cmfcacceleratorkeyassignctrl,](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a> Cmfcacceleratorkeyassignctrl, :: GetAccel

Récupère la `ACCEL` structure d’une touche de raccourci enfoncée dans l’objet [cmfcacceleratorkeyassignctrl,](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Valeur renvoyée

`ACCEL`Structure qui décrit la touche de raccourci.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour récupérer la `ACCEL` structure d’une touche de raccourci entrée par l’utilisateur dans votre `CMFCAcceleratorKeyAssignCtrl` objet.

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a> Cmfcacceleratorkeyassignctrl, :: IsFocused

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a> Cmfcacceleratorkeyassignctrl, :: IsKeyDefined

Détermine si une touche de raccourci a été définie dans l’objet [cmfcacceleratorkeyassignctrl,](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’utilisateur a déjà appuyé sur une combinaison valide de touches qui définissent une touche de raccourci ; Sinon, 0.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour déterminer si l’utilisateur a entré une touche de raccourci valide dans votre `CMFCAcceleratorKeyAssignCtrl` objet. Si une touche de raccourci existe, vous pouvez utiliser la méthode [cmfcacceleratorkeyassignctrl, :: GetAccel](#getaccel) pour obtenir la `ACCEL` structure associée à cette touche de raccourci.

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a> Cmfcacceleratorkeyassignctrl, ::P reTranslateMessage

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

dans *PMSG*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a> Cmfcacceleratorkeyassignctrl, :: ResetKey

Réinitialise la touche de raccourci.

```cpp
void ResetKey();
```

### <a name="remarks"></a>Notes

La fonction efface le texte du contrôle d’édition. Cela comprend toutes les touches de raccourci sur lesquelles l’utilisateur a appuyé.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Cmfcacceleratorkey,, classe](../../mfc/reference/cmfcacceleratorkey-class.md)
