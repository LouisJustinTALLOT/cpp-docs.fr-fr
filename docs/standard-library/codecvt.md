---
title: '&lt;codecvt&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- codecvt
- <codecvt>
dev_langs:
- C++
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 97a8ef1f8ba49da54e106886f1e3cf488049f92d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ltcodecvtgt"></a>&lt;codecvt&gt;

Définit plusieurs classes de modèle qui décrivent les objets basés sur la classe de modèle [codecvt](../standard-library/codecvt-class.md). Ces objets peuvent servir de [facettes de paramètres régionaux](../standard-library/locale-class.md#facet_class) pour contrôler les conversions entre une séquence de valeurs de type `Elem` et une séquence de valeurs de type `char`.

## <a name="syntax"></a>Syntaxe

```cpp
#include <codecvt>

```

## <a name="remarks"></a>Notes

Les facettes de paramètres régionaux déclarées dans cet en-tête effectuent la conversion entre plusieurs codages de caractère. Pour les caractères larges (stockés dans le programme en entiers de taille fixe) :

- UCS-4 est codé en Unicode (ISO 10646) dans le programme sous la forme d’un entier 32 bits.

- UCS-2 est codé en Unicode dans le programme sous la forme d’un entier 16 bits.

- UTF-16 est codé en Unicode dans le programme sous la forme d’un ou plusieurs entiers 16 bits. (Notez que cela ne répond pas à toutes les exigences d’un codage de caractères larges valide pour C Standard ou C++ Standard. Toutefois, ce codage est largement utilisé sous cette forme.)

Pour les flux d’octets (stockés dans un fichier, transmis sous la forme d’une séquence d’octets ou stockés dans le programme dans un tableau de `char`) :

- UTF-8 est codé en Unicode au sein d’un flux d’octets sous la forme d’un ou plusieurs octets 8 bits avec un ordre d’octet déterministe.

- UTF-16LE est codé en Unicode dans un flux d’octets au format UTF-16 avec chaque entier 16 bits présenté sous la forme de deux octets 8 bits, l’octet le moins significatif en premier.

- UTF-16BE est codé en Unicode dans un flux d’octets au format UTF-16 avec chaque entier 16 bits présenté sous la forme de deux octets 8 bits, l’octet le plus significatif en premier.

### <a name="enumerations"></a>Énumérations

|||
|-|-|
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|Spécifie des informations de configuration pour les facettes de paramètres régionaux.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[codecvt_utf8](codecvt-utf8-class.md)|Représente une facette de paramètres régionaux qui effectue la conversion entre des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets codé au format UTF-8.|
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|Représente une facette de paramètres régionaux qui effectue la conversion entre des caractères larges codés au format UTF-16 et un flux d’octets codé au format UTF-8.|
|[codecvt_utf16](codecvt-utf16-class.md)|Représente une facette de paramètres régionaux qui effectue la conversion entre des caractères larges codés au format UCS-2 ou UCS-4 et un flux d’octets codé au format UTF-16LE ou UTF-16BE.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<codecvt>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
