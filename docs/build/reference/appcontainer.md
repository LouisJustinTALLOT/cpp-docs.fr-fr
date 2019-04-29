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
ms.openlocfilehash: eb922a29b00fee63effae302505f25c98b04523e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274025"
---
# <a name="appcontainer"></a>/APPCONTAINER

Marque un fichier exécutable qui doit s’exécuter dans un conteneur d’application, par exemple, une application Microsoft Store ou Windows universelles.

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Notes

Un fichier exécutable dont l’option **/APPCONTAINER** est définie ne peut être exécuté que dans un conteneur d’application, ce qui correspond à l’environnement d’isolation des processus introduit dans Windows 8. Pour les applications Microsoft Store et Windows universelles, cette option doit être définie.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)<br/>
[Qu’est-ce qu’une application Windows universelle ?](/windows/uwp/get-started/universal-application-platform-guide)
