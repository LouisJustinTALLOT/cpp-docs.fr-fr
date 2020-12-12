---
description: En savoir plus sur:/APPCONTAINER
title: /APPCONTAINER
ms.date: 11/04/2016
f1_keywords:
- /APPCONTAINER
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
ms.openlocfilehash: f9ea7ff8cac45e45626f15745f77d2230afc1d4b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187167"
---
# <a name="appcontainer"></a>/APPCONTAINER

Marque un fichier exécutable qui doit s’exécuter dans un conteneur d’application, par exemple, une Microsoft Store ou une application Windows universelle.

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Notes

Un fichier exécutable dont l’option **/APPCONTAINER** est définie ne peut être exécuté que dans un conteneur d’application, ce qui correspond à l’environnement d’isolation des processus introduit dans Windows 8. Pour les Microsoft Store et les applications Windows universelles, cette option doit être définie.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)<br/>
[Qu’est-ce qu’une application Windows universelle ?](/windows/uwp/get-started/universal-application-platform-guide)
