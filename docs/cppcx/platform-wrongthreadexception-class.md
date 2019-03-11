---
title: Platform::WrongThreadException, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
ms.openlocfilehash: dde8c9afff6be083580042a958f59e057bc44350
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743954"
---
# <a name="platformwrongthreadexception-class"></a>Platform::WrongThreadException, classe

Levée lorsqu'un thread effectue un appel via un pointeur d'interface qui concerne un objet proxy qui n'appartient pas à l'apartment du thread.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez l'exception [COMException](../cppcx/platform-comexception-class.md).

### <a name="requirements"></a>Spécifications

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Platform::COMException, classe](../cppcx/platform-comexception-class.md)
