---
title: COleDialog, classe
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: c798c1ad81395465e7aa5405ab786ddfb67b71d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494703"
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
|[COleDialog::GetLastError](#getlasterror)|Obtient le code d’erreur retourné par la boîte de dialogue.|

## <a name="remarks"></a>Notes

La bibliothèque Microsoft Foundation Class fournit plusieurs classes dérivées de `COleDialog`:

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

## <a name="requirements"></a>Configuration requise

**En-tête :** afxodlgs.h

##  <a name="getlasterror"></a>  COleDialog::GetLastError

Appelez le `GetLastError` fonction membre pour obtenir des informations d’erreur supplémentaires lorsque `DoModal` retourne IDABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Valeur de retour

Les codes d’erreur retournés par `GetLastError` dépendent de la boîte de dialogue spécifique affichée.

### <a name="remarks"></a>Notes

Consultez le `DoModal` fonction membre dans les classes dérivées pour plus d’informations sur les messages d’erreur spécifiques.

## <a name="see-also"></a>Voir aussi

[CCommonDialog, classe](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

