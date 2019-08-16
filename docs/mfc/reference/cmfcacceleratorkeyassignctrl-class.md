---
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
ms.openlocfilehash: 5e57bf149fdbc293692c613afcabcf2d11d32221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505473"
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

## <a name="requirements"></a>Configuration requise

**En-tête:** afxacceleratorkeyassignctrl. h

##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Construit un objet [cmfcacceleratorkeyassignctrl,](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
CMFCAcceleratorKeyAssignCtrl();
```

##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel

Récupère la `ACCEL` structure d’une touche de raccourci enfoncée dans l’objet [cmfcacceleratorkeyassignctrl,](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Valeur de retour

`ACCEL` Structure qui décrit la touche de raccourci.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour récupérer la `ACCEL` structure d’une touche de raccourci entrée par l’utilisateur dans `CMFCAcceleratorKeyAssignCtrl` votre objet.

##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused

Pour plus d’informations, consultez le code source situé dans le dossier **VC\\ATLMFC\\SRC\\MFC** de votre installation de Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Détermine si une touche de raccourci a été définie dans l’objet [cmfcacceleratorkeyassignctrl,](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’utilisateur a déjà appuyé sur une combinaison valide de touches qui définissent une touche de raccourci; Sinon, 0.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour déterminer si l’utilisateur a entré une touche de raccourci valide `CMFCAcceleratorKeyAssignCtrl` dans votre objet. Si une touche de raccourci existe, vous pouvez utiliser la méthode [cmfcacceleratorkeyassignctrl,:: GetAccel](#getaccel) pour `ACCEL` obtenir la structure associée à cette touche de raccourci.

##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Pour plus d’informations, consultez le code source situé dans le dossier **VC\\ATLMFC\\SRC\\MFC** de votre installation de Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

dans *PMSG*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey

Réinitialise la touche de raccourci.

```
void ResetKey();
```

### <a name="remarks"></a>Notes

La fonction efface le texte du contrôle d’édition. Cela comprend toutes les touches de raccourci sur lesquelles l’utilisateur a appuyé.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey, classe](../../mfc/reference/cmfcacceleratorkey-class.md)
