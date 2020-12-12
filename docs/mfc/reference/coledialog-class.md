---
description: 'En savoir plus sur : classe COleDialog'
title: COleDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: 9bdb532d58136ac2aac622fa88f674e60ec7221e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227297"
---
# <a name="coledialog-class"></a>COleDialog, classe

Fournit les fonctionnalités communes aux boîtes de dialogue pour OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDialog :: GetLastError](#getlasterror)|Obtient le code d’erreur retourné par la boîte de dialogue.|

## <a name="remarks"></a>Notes

L’bibliothèque MFC (Microsoft Foundation Class) fournit plusieurs classes dérivées de `COleDialog` :

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

Pour plus d’informations sur les boîtes de dialogue spécifiques à OLE, consultez l’article [boîtes de dialogue dans OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Spécifications

**En-tête :** afxodlgs. h

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a> COleDialog :: GetLastError

Appelez la `GetLastError` fonction membre pour obtenir des informations supplémentaires sur l’erreur quand `DoModal` retourne IDABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Valeur renvoyée

Les codes d’erreur retournés par `GetLastError` dépendent de la boîte de dialogue spécifique affichée.

### <a name="remarks"></a>Notes

`DoModal`Pour plus d’informations sur les messages d’erreur spécifiques, consultez la fonction membre dans les classes dérivées.

## <a name="see-also"></a>Voir aussi

[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
