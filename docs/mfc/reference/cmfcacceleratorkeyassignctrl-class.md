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
ms.openlocfilehash: 2021a2069885c6314859a65d528cf03712c524b6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751737"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl, classe

La `CMFCAcceleratorKeyAssignCtrl` classe étend la [classe CEdit](../../mfc/reference/cedit-class.md) pour prendre en charge des boutons système supplémentaires tels que ALT, CONTROL et SHIFT.

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
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour traduire les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Réinitialise la touche de raccourci.|

## <a name="remarks"></a>Notes

Cette classe étend les fonctionnalités de la classe `CEdit` en prenant en charge les touches de raccourci, aussi appelées touches accélérateur. La `CMFCAcceleratorKeyAssignCtrl` classe fonctionne comme une [classe CEdit](../../mfc/reference/cedit-class.md) et il peut également reconnaître les boutons du système.

Cette classe mappe les combinaisons de touches de raccourci physiques à des valeurs de chaîne. Par exemple, supposons que la combinaison de touches Alt+B est mappé à la chaîne « Alt+B ». Quand l'utilisateur appuie sur cette combinaison de touches dans un objet `CMFCAcceleratorKeyAssignCtrl`, « Alt+B » est présenté à l'utilisateur. Pour plus d’informations sur la cartographie entre les touches de raccourci et un format de chaîne, voir [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md).

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

**En-tête:** afxacceleratorkeyassignctrl.h

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Construit un objet [CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel

Récupère la `ACCEL` structure pour une clé de raccourci pressée dans l’objet [CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Valeur de retour

Une `ACCEL` structure qui décrit la clé de raccourci.

### <a name="remarks"></a>Notes

Utilisez cette fonction `ACCEL` pour récupérer la structure pour une `CMFCAcceleratorKeyAssignCtrl` clé raccourcie que l’utilisateur a saisie dans votre objet.

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Détermine si une clé de raccourci a été définie dans l’objet [CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’utilisateur a déjà appuyé sur une combinaison valide de touches qui définissent une clé de raccourci; sinon 0.

### <a name="remarks"></a>Notes

Utilisez cette fonction pour déterminer si l’utilisateur `CMFCAcceleratorKeyAssignCtrl` a saisi une clé de raccourci valide dans votre objet. Si une clé de raccourci existe, vous pouvez utiliser la méthode [CMFCAcceleratorKeyAssignCtrl ::GetAccel](#getaccel) méthode pour obtenir la `ACCEL` structure associée à cette clé de raccourci.

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Paramètres

[dans] *pMsg*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey

Réinitialise la touche de raccourci.

```cpp
void ResetKey();
```

### <a name="remarks"></a>Notes

La fonction efface le texte de contrôle de modification. Cela comprend toutes les touches de raccourci que l’utilisateur a pressées.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey, classe](../../mfc/reference/cmfcacceleratorkey-class.md)
