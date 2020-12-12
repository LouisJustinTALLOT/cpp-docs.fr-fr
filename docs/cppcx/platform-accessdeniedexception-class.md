---
description: 'En savoir plus sur : classe Platform :: AccessDeniedException'
title: Platform::AccessDeniedException, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
ms.openlocfilehash: 2dd1e543093000521bceb0abed128a1dac27a6e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276787"
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException, classe

Levée lorsque l'accès à une ressource ou à une fonctionnalité est refusé.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable
```

### <a name="remarks"></a>Notes

Si vous rencontrez cette exception, vérifiez que vous avez demandé la fonctionnalité appropriée et que avez effectué les déclarations requises dans le manifeste de package de votre application. Pour plus d'informations, consultez [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="see-also"></a>Voir aussi

[Platform :: COMException, classe](../cppcx/platform-comexception-class.md)
