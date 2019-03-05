---
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
ms.openlocfilehash: 42239ff060d5e081f273ce9dd7d87d1dbbeca716
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302154"
---
# <a name="colecontrolmodule-class"></a>COleControlModule, classe

Classe de base à partir de laquelle vous dérivez un objet de module de contrôle OLE.

## <a name="syntax"></a>Syntaxe

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions membres pour l’initialisation du module de votre contrôle. Chaque module de contrôle OLE qui utilise les classes Microsoft Foundation ne peut contenir un objet dérivé de `COleControlModule`. Cet objet est construit lorsque les autres objets globaux C++ sont construites. Déclarez votre dérivée `COleControlModule` objet au niveau global.

Pour plus d’informations sur l’utilisation de la `COleControlModule` de classe, consultez le [CWinApp](../../mfc/reference/cwinapp-class.md) classe et l’article [contrôles ActiveX](../../mfc/mfc-activex-controls.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>Spécifications

**En-tête :** afxctl.h

## <a name="see-also"></a>Voir aussi

[Exemple MFC TESTHELP](../../visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
