---
title: SafeIntException, classe
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
ms.openlocfilehash: 80a1573c2f43b1f4b31731083974f87ba389fac2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566658"
---
# <a name="safeintexception-class"></a>SafeIntException, classe

Le `SafeInt` classe utilise `SafeIntException` pour identifier la raison pour laquelle une opération mathématique ne peut pas être effectuée.

> [!NOTE]
> La dernière version de cette bibliothèque se trouve dans [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Syntaxe

```cpp
class SafeIntException;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                    | Description
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Crée un objet `SafeIntException`.

## <a name="remarks"></a>Notes

Le [classe SafeInt](../windows/safeint-class.md) est la seule classe qui utilise le `SafeIntException` classe.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SafeIntException`

## <a name="requirements"></a>Configuration requise

**En-tête :** safeint.h

**Namespace :** msl::utilities

## <a name="safeintexception"></a>SafeIntException::SafeIntException

Crée un objet `SafeIntException`.

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Paramètres

*code*<br/>
[in] Une valeur de données énuméré qui décrit l’erreur qui s’est produite.

### <a name="remarks"></a>Notes

Les valeurs possibles pour *code* sont définis dans le fichier Safeint.h. Pour plus de commodité, les valeurs possibles sont également répertoriés ici.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
