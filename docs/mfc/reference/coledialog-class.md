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
ms.openlocfilehash: 6a1983d426e97dd8063aee2857dc36557aa20677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366096"
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

La Bibliothèque de classe Microsoft `COleDialog`Foundation offre plusieurs classes dérivées de :

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

Pour plus d’informations sur les boîtes de dialogue spécifiques à l’OLOL, voir l’article [Dialog Boxes in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Spécifications

**En-tête:** afxodlgs.h

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a>COleDialog::GetLastError

Appelez `GetLastError` la fonction membre pour `DoModal` obtenir des informations d’erreur supplémentaires lors de la déclaration idABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Valeur de retour

Les codes d’erreur retournés dépendent `GetLastError` de la boîte de dialogue spécifique affichée.

### <a name="remarks"></a>Notes

Consultez `DoModal` la fonction de membre dans les classes dérivées pour obtenir des informations sur des messages d’erreur spécifiques.

## <a name="see-also"></a>Voir aussi

[Classe CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
