---
description: 'En savoir plus sur : classe Platform :: ChangedStateException'
title: Platform::ChangedStateException, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
ms.openlocfilehash: baabf54cacfc4dd03256b569fb868c402ea98a97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284029"
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException, classe

Exception levée lorsque l'état interne d'un objet a changé, ce qui entraîne l'invalidation des résultats de la méthode.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Notes

Par exemple, cette exception est levée lorsque les méthodes d'un itérateur de collection ou d'une vue de collection sont appelées après la modification d'une collection parente, invalidant ainsi les résultats de la méthode.

Pour plus d'informations, consultez la classe [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="see-also"></a>Voir aussi

[Platform :: COMException, classe](../cppcx/platform-comexception-class.md)
