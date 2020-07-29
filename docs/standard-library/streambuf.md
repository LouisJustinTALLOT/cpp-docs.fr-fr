---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 1121bd4e782fca57588d05fb29b5b9b6cdec18e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215606"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Incluez l’en-tête standard iostreams \<streambuf> pour définir le modèle de classe [basic_streambuf](../standard-library/basic-streambuf-class.md), qui est de base au fonctionnement des classes iostreams. Cet en-tête est généralement inclus pour vous par l'un des autres en-tête iostream ; vous devez rarement l'inclure directement.

## <a name="syntax"></a>Syntaxe

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Spécialisation de `basic_streambuf` qui utilise **`char`** comme paramètres de modèle.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|Spécialisation de `basic_streambuf` qui utilise **`wchar_t`** comme paramètres de modèle.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[Classe basic_streambuf](basic-streambuf-class.md)|Le modèle de classe décrit une classe de base abstraite pour dériver une mémoire tampon de flux qui contrôle la transmission d’éléments vers et à partir d’une représentation spécifique d’un flux.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
