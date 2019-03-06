---
title: /APPCONTAINER
ms.date: 11/04/2016
f1_keywords:
- /APPCONTAINER
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
ms.openlocfilehash: ad451f5900841abe3f0fe10ae99fa0183e14e5c5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412588"
---
# <a name="appcontainer"></a>/APPCONTAINER

Marque un fichier exécutable qui doit s’exécuter dans un conteneur d’application, par exemple, une application Microsoft Store ou Windows universelles.

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Notes

Un fichier exécutable dont l’option **/APPCONTAINER** est définie ne peut être exécuté que dans un conteneur d’application, ce qui correspond à l’environnement d’isolation des processus introduit dans Windows 8. Pour les applications Microsoft Store et Windows universelles, cette option doit être définie.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](../../build/reference/editbin-options.md)<br/>
[Qu’est-ce qu’une application Windows universelle ?](/windows/uwp/get-started/universal-application-platform-guide)
