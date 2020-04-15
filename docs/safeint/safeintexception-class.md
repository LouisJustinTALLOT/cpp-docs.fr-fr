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
ms.openlocfilehash: e118d7e3cce47ebb93cef16319a8fc45aab1118b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349945"
---
# <a name="safeintexception-class"></a>SafeIntException, classe

La classe `SafeInt` utilise `SafeIntException` pour identifier la raison pour laquelle une opération mathématique ne peut pas être effectuée.

> [!NOTE]
> La dernière version de cette [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)bibliothèque est située à .

## <a name="syntax"></a>Syntaxe

```cpp
class SafeIntException;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                                                    | Description
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Crée un objet `SafeIntException` .

## <a name="remarks"></a>Notes

La [classe SafeInt](../safeint/safeint-class.md) est la seule classe qui utilise la classe `SafeIntException`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SafeIntException`

## <a name="requirements"></a>Spécifications

**En-tête :** safeint.h

**Espace de noms :** msl::utilities

## <a name="safeintexceptionsafeintexception"></a><a name="safeintexception"></a>SafeIntException::SafeIntException

Crée un objet `SafeIntException` .

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Paramètres

*Code*<br/>
[in] Une valeur de données énumérées qui décrit l’erreur qui s’est produite.

### <a name="remarks"></a>Notes

Les valeurs possibles pour *code* sont définies dans le fichier Safeint.h. Pour des raisons pratiques, les valeurs possibles sont également répertoriées ici.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
