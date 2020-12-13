---
description: 'En savoir plus sur : classe Cmfcacceleratorkey,'
title: Cmfcacceleratorkey,, classe
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
ms.openlocfilehash: cb7fc24c4cb4d092c5f109ad892b3778d74a906f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336609"
---
# <a name="cmfcacceleratorkey-class"></a>Cmfcacceleratorkey,, classe

Classe d’assistance qui implémente le mappage et la mise en forme des clés virtuelles.

## <a name="syntax"></a>Syntaxe

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Cmfcacceleratorkey, :: Cmfcacceleratorkey,](#cmfcacceleratorkey)|Construit un objet `CMFCAcceleratorKey`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Cmfcacceleratorkey, :: format](#format)|Convertit la structure d’accélération en sa représentation visuelle.|
|[Cmfcacceleratorkey, :: SetAccelerator](#setaccelerator)|Définit la touche de raccourci de l' `CMFCAcceleratorKey` objet.|

## <a name="remarks"></a>Notes

Les touches d’accès rapide sont également appelées touches de raccourci. Si vous souhaitez afficher les raccourcis clavier entrés par un utilisateur, la [classe cmfcacceleratorkeyassignctrl,](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mappe les raccourcis clavier, tels que Alt + Maj + s, à un format de texte personnalisé, tel que « Alt + Maj + s ». Chaque `CMFCAcceleratorKey` objet mappe une touche de raccourci unique à un format texte.

Pour plus d’informations sur l’utilisation des touches de raccourci et des tables d’accélérateurs, consultez [CKeyboardManager, classe](../../mfc/reference/ckeyboardmanager-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCAcceleratorKey` objet et comment utiliser sa `Format` méthode.

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Spécifications

**En-tête :** afxacceleratorkey. h

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a> Cmfcacceleratorkey, :: Cmfcacceleratorkey,

Construit un objet [cmfcacceleratorkey,](../../mfc/reference/cmfcacceleratorkey-class.md) .

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Paramètres

*lpAccel*<br/>
dans Pointeur vers une touche de raccourci.

### <a name="remarks"></a>Notes

Si vous ne fournissez pas de touche de raccourci quand vous créez un `CMFCAccleratorKey` , utilisez la méthode [cmfcacceleratorkey, :: SetAccelerator](#setaccelerator) pour associer une touche de raccourci à votre `CMFCAcceleratorKey` objet.

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a> Cmfcacceleratorkey, :: format

Convertit la structure d’accélération en sa valeur de chaîne associée.

```cpp
void Format(CString& str) const;
```

### <a name="parameters"></a>Paramètres

*str*<br/>
à Référence à un `CString` objet où la méthode écrit la touche de raccourci traduite.

### <a name="remarks"></a>Notes

Cette méthode récupère le format de chaîne de la touche de raccourci associée. Vous pouvez définir le format de chaîne d’un objet [cmfcacceleratorkey,](../../mfc/reference/cmfcacceleratorkey-class.md) à l’aide du constructeur ou de la méthode [Cmfcacceleratorkey, :: SetAccelerator](#setaccelerator).

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a> Cmfcacceleratorkey, :: SetAccelerator

Définit la touche de raccourci pour l’objet [cmfcacceleratorkey,](../../mfc/reference/cmfcacceleratorkey-class.md) .

```cpp
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Paramètres

*lpAccel*<br/>
dans Pointeur vers une touche de raccourci.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir la touche de raccourci pour un `CMFCAcceleratorKey` si vous n’avez pas fourni de touche de raccourci lorsque vous avez créé le `CMFCAcceleratorKey` .

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager, classe](../../mfc/reference/ckeyboardmanager-class.md)
