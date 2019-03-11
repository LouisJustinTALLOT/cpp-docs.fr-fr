---
title: Platform::DisconnectedException, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
ms.openlocfilehash: 56276a7d09cc82e05886c2c67a4784993083adb5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752010"
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

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Platform::COMException, classe](../cppcx/platform-comexception-class.md)
