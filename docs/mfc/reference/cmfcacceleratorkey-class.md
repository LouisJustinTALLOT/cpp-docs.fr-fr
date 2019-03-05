---
title: Cmfcacceleratorkey, classe
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
ms.openlocfilehash: 6a99ad00a43ac7912320ee469d542b6bf9cca3de
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292261"
---
# <a name="cmfcacceleratorkey-class"></a>Cmfcacceleratorkey, classe

Une classe d’assistance qui implémente le mappage de clé virtuel et la mise en forme.

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
|[CMFCAcceleratorKey::Format](#format)|Convertit la structure d’accélération à sa représentation visuelle.|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Définit la touche de raccourci pour le `CMFCAcceleratorKey` objet.|

## <a name="remarks"></a>Notes

Touches accélérateur sont également appelées touches de raccourci. Si vous souhaitez afficher les raccourcis clavier entrées par un utilisateur, le [cmfcacceleratorkeyassignctrl, classe](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) maps raccourcis clavier, tels que Alt + Maj + S, dans un format de texte personnalisé, tel que « Alt + Maj + S ». Chaque `CMFCAcceleratorKey` objet mappe une touche de raccourci unique dans un format de texte.

Pour plus d’informations sur l’utilisation des touches de raccourci et les tables d’accélérateurs, consultez [ckeyboardmanager, classe](../../mfc/reference/ckeyboardmanager-class.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment construire un `CMFCAcceleratorKey` objet et comment utiliser son `Format` (méthode).

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Spécifications

**En-tête :** afxacceleratorkey.h

##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey

Construit un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objet.

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Paramètres

*lpAccel*<br/>
[in] Pointeur vers une touche de raccourci.

### <a name="remarks"></a>Notes

Si vous ne fournissez pas une touche de raccourci lorsque vous créez un `CMFCAccleratorKey`, utilisez le [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) méthode pour associer une touche de raccourci avec votre `CMFCAcceleratorKey` objet.

##  <a name="format"></a>  CMFCAcceleratorKey::Format

Convertit la structure d’accélération à sa valeur de chaîne associée.

```
void Format(CString& str) const;
```

### <a name="parameters"></a>Paramètres

*str*<br/>
[out] Une référence à un `CString` objet dans lequel la méthode écrit la touche de raccourci traduite.

### <a name="remarks"></a>Notes

Cette méthode récupère le format de chaîne de la touche de raccourci associé. Vous pouvez définir le format de chaîne d’un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) de l’objet à l’aide du constructeur ou la méthode [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).

##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator

Définit la touche de raccourci pour le [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objet.

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Paramètres

*lpAccel*<br/>
[in] Pointeur vers une touche de raccourci.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour définir la touche de raccourci pour un `CMFCAcceleratorKey` si vous n’avez pas fourni une touche de raccourci lorsque vous avez créé le `CMFCAcceleratorKey`.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager, classe](../../mfc/reference/ckeyboardmanager-class.md)
