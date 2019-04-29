---
title: '&lt;ostream&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- ostream/std::operator&lt;&lt;
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
ms.openlocfilehash: ee1a9a6829dbef13b034300d696c43ddba48d9d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370946"
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt;, opérateurs

||
|-|
|[operator&lt;&lt;](#op_lt_lt)|

## <a name="op_lt_lt"></a>  operator&lt;&lt;

Écrit différents types dans le flux.

```cpp
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```

### <a name="parameters"></a>Paramètres

*_Ch*<br/>
Un caractère.

*_Elem*<br/>
Type de l’élément.

*_Ostr*<br/>
Objet `basic_ostream`.

*str*<br/>
Chaîne caractère.

*_Tr*<br/>
Caractéristiques du caractère.

*val*<br/>
Type

### <a name="return-value"></a>Valeur de retour

flux.

### <a name="remarks"></a>Notes

La classe `basic_ostream` définit également plusieurs opérateurs d’insertion. Pour plus d’informations, consultez [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt).

La fonction de modèle

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```

Détermine la longueur N = `traits_type::` [longueur](../standard-library/char-traits-struct.md#length)(`str`) de la séquence à partir *str*et insère la séquence. Si N < `_Ostr.`[width](../standard-library/ios-base-class.md#width), la fonction insère également une répétition de caractères de remplissage -N `_Ostr.width`. La répétition précède la séquence si (`_Ostr`. [flags](../standard-library/ios-base-class.md#flags) & `adjustfield` != [left](../standard-library/ios-functions.md#left). Sinon, la répétition suit la séquence. La fonction retourne *_Ostr*.

La fonction de modèle

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

insère l’élément `_Ch`. Si 1 < `_Ostr.width`, la fonction insère également une répétition de caractères de remplissage - 1 `_Ostr.width`. La répétition précède la séquence si `_Ostr.flags & adjustfield != left`. Sinon, la répétition suit la séquence. Elle retourne *_Ostr*.

La fonction de modèle

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```

se comporte comme

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

sauf que chaque élément *_Ch* de la séquence à partir *str* est converti en un objet de type `Elem` en appelant `_Ostr.` [put](../standard-library/basic-ostream-class.md#put)(`_Ostr.` [élargir](../standard-library/basic-ios-class.md#widen)(`_Ch`)).

La fonction de modèle

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```

se comporte comme

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

à ceci près que *_Ch* est converti en un objet de type `Elem` en appelant `_Ostr.put`( `_Ostr.widen`( `_Ch`)).

La fonction de modèle

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```

se comporte comme

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```

(Elle n’a pas besoin d’élargir les éléments avant de les insérer.)

La fonction de modèle

```cpp
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```

se comporte comme

```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```

(Il n’a pas besoin d’élargir *_Ch* avant de l’insérer.)

La fonction de modèle

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```

Retourne `_Ostr` << (`const char *`) `str`.

La fonction de modèle

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```

Retourne `_Ostr` << (`char`) `_Ch`.

La fonction de modèle

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```

Retourne `_Ostr` << (`const char *`) `str`.

La fonction de modèle

```cpp
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```

Retourne `_Ostr` << (`char`) `_Ch`.

La fonction de modèle

```cpp
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```

retourne `_Ostr` `<<` `val` (et convertit une [référence RValue](../cpp/rvalue-reference-declarator-amp-amp.md) à `_Ostr` en lvalue dans le processus).

### <a name="example"></a>Exemple

Consultez [flush](../standard-library/ostream-functions.md#flush) pour obtenir un exemple qui utilise `operator<<`.

## <a name="see-also"></a>Voir aussi

[\<ostream>](../standard-library/ostream.md)<br/>
