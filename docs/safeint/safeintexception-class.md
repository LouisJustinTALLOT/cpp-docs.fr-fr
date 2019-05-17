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
ms.openlocfilehash: 2998bbb83fd568d7ff627d6598c32fb5b17c1e40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515564"
---
# <a name="safeintexception-class"></a>SafeIntException, classe

La classe `SafeInt` utilise `SafeIntException` pour identifier la raison pour laquelle une opération mathématique ne peut pas être effectuée.

> [!NOTE]
> La dernière version de cette bibliothèque se trouve dans [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt).

## <a name="syntax"></a>Syntaxe

```cpp
class SafeIntException;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Name                                                    | Description
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Crée un objet `SafeIntException`.

## <a name="remarks"></a>Remarques

La [classe SafeInt](../safeint/safeint-class.md) est la seule classe qui utilise la classe `SafeIntException`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SafeIntException`

## <a name="requirements"></a>Spécifications

**En-tête :** safeint.h

**Espace de noms :** msl::utilities

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
[in] Une valeur de données énumérées qui décrit l’erreur qui s’est produite.

### <a name="remarks"></a>Remarques

Les valeurs possibles pour *code* sont définies dans le fichier Safeint.h. Pour des raisons pratiques, les valeurs possibles sont également répertoriées ici.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
