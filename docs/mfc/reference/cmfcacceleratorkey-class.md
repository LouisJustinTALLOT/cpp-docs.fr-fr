---
title: CMFCAcceleratorKey, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: a814618d3bda27d5b4ace12209dd93343ef2eef9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751781"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey, classe

Une classe d’aide qui met en œuvre la cartographie et le formatage des clés virtuelles.

## <a name="syntax"></a>Syntaxe

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Construit un objet `CMFCAcceleratorKey`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCAcceleratorKey::Format](#format)|Traduit la structure ACCEL à sa représentation visuelle.|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Définit la clé de `CMFCAcceleratorKey` raccourci pour l’objet.|

## <a name="remarks"></a>Notes

Les touches d’accélérateur sont également connues sous le nom de touches de raccourci. Si vous souhaitez afficher des raccourcis clavier qu’un utilisateur entre, le [CMFCAcceleratorKeyAssignCtrl Class](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) cartes des raccourcis clavier, tels qu’Alt-Shift-S, à un format texte personnalisé, tel que "Alt - Shift ' S". Chaque `CMFCAcceleratorKey` objet cartographie une seule clé de raccourci d’un format de texte.

Pour plus d’informations sur la façon d’utiliser des touches de raccourci et des tables d’accélérateur, voir [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment `CMFCAcceleratorKey` construire un objet `Format` et comment utiliser sa méthode.

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Spécifications

**En-tête:** afxacceleratorkey.h

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey

Construit un objet [CMFCAcceleratorKey.](../../mfc/reference/cmfcacceleratorkey-class.md)

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Paramètres

*lpAccel*<br/>
[dans] Un pointeur à une clé de raccourci.

### <a name="remarks"></a>Notes

Si vous ne fournissez pas une `CMFCAccleratorKey`clé de raccourci lorsque vous créez un, utilisez la méthode [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) méthode pour associer une clé de raccourci avec votre `CMFCAcceleratorKey` objet.

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a>CMFCAcceleratorKey::Format

Traduit la structure ACCEL à sa valeur de chaîne associée.

```cpp
void Format(CString& str) const;
```

### <a name="parameters"></a>Paramètres

*Str*<br/>
[out] Une référence `CString` à un objet où la méthode écrit la clé de raccourci traduite.

### <a name="remarks"></a>Notes

Cette méthode récupère le format de chaîne de la clé de raccourci associée. Vous pouvez définir le format de chaîne d’un objet [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) en utilisant soit le constructeur ou la méthode [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator

Définit la clé de raccourci pour l’objet [CMFCAcceleratorKey.](../../mfc/reference/cmfcacceleratorkey-class.md)

```cpp
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Paramètres

*lpAccel*<br/>
[dans] Un pointeur à une clé de raccourci.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir la `CMFCAcceleratorKey` clé de raccourci pour un si `CMFCAcceleratorKey`vous n’avez pas fourni une clé de raccourci lorsque vous avez créé le .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
