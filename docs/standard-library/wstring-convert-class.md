---
description: 'En savoir plus sur : classe wstring_convert'
title: wstring_convert, classe
ms.date: 11/04/2016
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
ms.openlocfilehash: 53c3e311967295294d158bb0342d365d45f5e031
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187739"
---
# <a name="wstring_convert-class"></a>wstring_convert, classe

Le modèle de classe `wstring_convert` effectue des conversions entre une chaîne étendue et une chaîne d’octets.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Paramètres

*Codecvt*\
La facette [locale](../standard-library/locale-class.md) qui représente l’objet de conversion.

*Elem*\
Type d'élément à caractères larges.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui contrôle les conversions entre les objets de chaîne étendues des objets de chaîne de classe `std::basic_string<Elem>` et d’octets de la classe `std::basic_string<char>` (également appelée `std::string` ). Le modèle de classe définit les types `wide_string` et `byte_string` comme synonymes pour ces deux types. La conversion entre une séquence de valeurs `Elem` (stockée dans un objet `wide_string`) et des séquences multioctets (stockées dans un objet `byte_string`) est effectuée par un objet de classe `Codecvt<Elem, char, std::mbstate_t>`, qui répond aux exigences de la facette de conversion de code standard `std::codecvt<Elem, char, std::mbstate_t>`.

Un objet de ce modèle de classe stocke les éléments suivants :

- une chaîne d'octets à afficher en cas d'erreur ;

- une chaîne étendue à afficher en cas d'erreur ;

- un pointeur vers l’objet de conversion alloué (qui est libéré quand l’objet wbuffer_convert est détruit) ;

- un objet d’état de conversion de type [state_type](#state_type) ;

- un décompte des conversions.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[wstring_convert](#wstring_convert)|Construit un objet de type `wstring_convert`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[byte_string](#byte_string)|Type qui représente une chaîne d'octets.|
|[wide_string](#wide_string)|Type qui représente une chaîne étendue.|
|[state_type](#state_type)|Type qui représente l'état de conversion.|
|[int_type](#int_type)|Type qui représente un entier.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[from_bytes](#from_bytes)|Convertit une chaîne d'octets en chaîne étendue.|
|[to_bytes](#to_bytes)|Convertit une chaîne étendue en chaîne d'octets.|
|[converted](#converted)|Retourne le nombre de conversions réussies.|
|[state](#state)|Retourne un objet représentant l'état de la conversion.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="wstring_convertbyte_string"></a><a name="byte_string"></a> wstring_convert :: byte_string

Type qui représente une chaîne d'octets.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `std::basic_string<char>`.

## <a name="wstring_convertconverted"></a><a name="converted"></a> wstring_convert :: convertis

Retourne le nombre de conversions réussies.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de conversions ayant réussi.

### <a name="remarks"></a>Notes

Le nombre de conversions ayant réussi est stocké dans l'objet de compteur de conversions.

## <a name="wstring_convertfrom_bytes"></a><a name="from_bytes"></a> wstring_convert :: from_bytes

Convertit une chaîne d'octets en chaîne étendue.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Paramètres

*Poids*\
Séquence d'octets à élément unique à convertir.

*effectués*\
Séquence de caractères de style C et se terminant par null à convertir.

*BSTR*\
[byte_string](#byte_string) à convertir.

*premier*\
Premier caractère d'une plage de caractères à convertir.

*famille*\
Dernier caractère d'une plage de caractères à convertir.

### <a name="return-value"></a>Valeur renvoyée

Objet de chaîne étendue résultant de la conversion.

### <a name="remarks"></a>Notes

Si l’objet d' [État de conversion](../standard-library/wstring-convert-class.md) n’a *pas* été construit avec une valeur explicite, il est défini sur sa valeur par défaut (l’état de conversion initial) avant le début de la conversion. Dans le cas contraire, il reste inchangé.

Le nombre d'éléments d'entrée convertis correctement est stocké dans l'objet de compteur de conversions. Si aucune erreur de conversion ne se produit, la fonction membre retourne la chaîne étendue convertie. Sinon, si l'objet a été construit avec un initialiseur pour le message d'erreur de chaîne étendue, la fonction membre retourne l'objet de message d'erreur de chaîne étendue. Sinon, la fonction membre lève un objet de classe [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertint_type"></a><a name="int_type"></a> wstring_convert :: int_type

Type qui représente un entier.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `wide_string::traits_type::int_type`.

## <a name="wstring_convertstate"></a><a name="state"></a> wstring_convert :: State

Retourne un objet représentant l'état de la conversion.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’objet d’[état de conversion](../standard-library/wstring-convert-class.md) qui représente l’état de la conversion.

### <a name="remarks"></a>Notes

## <a name="wstring_convertstate_type"></a><a name="state_type"></a> wstring_convert :: state_type

Type qui représente l'état de conversion.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Notes

Le type décrit un objet qui peut représenter un état de conversion. Le type est un synonyme de `Codecvt::state_type`.

## <a name="wstring_convertto_bytes"></a><a name="to_bytes"></a> wstring_convert :: to_bytes

Convertit une chaîne étendue en chaîne d'octets.

```cpp
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```

### <a name="parameters"></a>Paramètres

*Char*\
Caractère large à convertir.

*Wptr*\
Séquence de style C, se terminant par null et commençant à `wptr`, à convertir.

*WSTR*\
[wide_string](#wide_string) à convertir.

*premier*\
Premier élément dans une plage d'éléments à convertir.

*famille*\
Dernier élément dans une plage d'éléments à convertir.

### <a name="remarks"></a>Notes

Si l’objet d' [État de conversion](../standard-library/wstring-convert-class.md) n’a *pas* été construit avec une valeur explicite, il est défini sur sa valeur par défaut (l’état de conversion initial) avant le début de la conversion. Dans le cas contraire, il reste inchangé.

Le nombre d'éléments d'entrée convertis correctement est stocké dans l'objet de compteur de conversions. Si aucune erreur de conversion ne se produit, la fonction membre retourne la chaîne d'octets convertie. Sinon, si l'objet a été construit avec un initialiseur pour le message d'erreur de chaîne d'octets, la fonction membre retourne l'objet de message d'erreur de chaîne d'octets. Sinon, la fonction membre lève un objet de classe [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertwide_string"></a><a name="wide_string"></a> wstring_convert :: wide_string

Type qui représente une chaîne étendue.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `std::basic_string<Elem>`.

## <a name="wstring_convertwstring_convert"></a><a name="wstring_convert"></a> wstring_convert :: wstring_convert

Construit un objet de type `wstring_convert`.

```cpp
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```

### <a name="parameters"></a>Paramètres

*\*Pcvt*\
Objet de type `Codecvt` pour effectuer la conversion.

*_State*\
Objet de type [state_type](#state_type) représentant l’état de la conversion.

*_Berr*\
[byte_string](#byte_string) à afficher en cas d’erreur.

*Werr*\
[wide_string](#wide_string) à afficher en cas d’erreur.

### <a name="remarks"></a>Notes

Le premier constructeur stocke *Pcvt_arg* dans l’[objet de conversion](../standard-library/wstring-convert-class.md)
