---
description: 'En savoir plus sur : classe COleControlModule'
title: COleControlModule, classe
ms.date: 11/04/2016
f1_keywords:
- OleControlModule
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
ms.openlocfilehash: f88296b7c0e897f82227343b31ca2f639902256e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227479"
---
# <a name="colecontrolmodule-class"></a>COleControlModule, classe

Classe de base à partir de laquelle vous dérivez un objet de module de contrôle OLE.

## <a name="syntax"></a>Syntaxe

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions membres pour l’initialisation de votre module de contrôle. Chaque module de contrôle OLE qui utilise les classes Microsoft Foundation ne peut contenir qu’un seul objet dérivé de `COleControlModule` . Cet objet est construit lorsque d’autres objets globaux C++ sont construits. Déclarez votre `COleControlModule` objet dérivé au niveau global.

Pour plus d’informations sur l’utilisation de la `COleControlModule` classe, consultez la classe [CWinApp](../../mfc/reference/cwinapp-class.md) et l’article [contrôles ActiveX](../../mfc/mfc-activex-controls.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>Spécifications

**En-tête :** afxctl. h

## <a name="see-also"></a>Voir aussi

[Exemple MFC TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
