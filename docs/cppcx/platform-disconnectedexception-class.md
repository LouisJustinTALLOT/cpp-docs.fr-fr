---
description: 'En savoir plus sur : plateforme ::D classe isconnectedException'
title: Platform::DisconnectedException, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
ms.openlocfilehash: 6ccfedc143d0245582c7c1f95110207d583949fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195318"
---
# <a name="platformdisconnectedexception-class"></a>Platform::DisconnectedException, classe

Levée quand un objet proxy COM essaie de faire référence à un serveur COM qui n'existe plus

## <a name="syntax"></a>Syntaxe

```
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Notes

Quand une classe A fait référence à une autre classe (classe B) qui se trouve dans un processus séparé, la classe A nécessite un objet proxy pour communiquer avec le serveur COM hors processus qui contient la classe B. Parfois, le serveur peut ne plus avoir suffisamment de mémoire, sans que la classe A ne s’en aperçoive. Dans ce cas, l'exception RPC_E_DISCONNECTED est levée et est traduite en Platform::DisconnectedException. Cela peut se produire dans un scénario dans lequel une source d'événement appelle un délégué qui lui a été passé, mais que le délégué a été supprimé une fois abonné à l'événement. Lorsque cela se produit, la source d'événement supprime ce délégué de sa liste d'appels.

Pour plus d'informations, consultez la classe [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="see-also"></a>Voir aussi

[Platform :: COMException, classe](../cppcx/platform-comexception-class.md)
