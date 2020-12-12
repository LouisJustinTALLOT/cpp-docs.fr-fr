---
description: 'En savoir plus sur : &lt; FStream&gt;'
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 98fe18306d50a9d6f1f8a360d4d29b6e865f6328
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324263"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Définit plusieurs classes qui prennent en charge les opérations iostreams sur des séquences stockées dans des fichiers externes.

## <a name="syntax"></a>Syntaxe

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Type `basic_filebuf` spécialisé sur les **`char`** paramètres de modèle.|
|[FStream](../standard-library/fstream-typedefs.md#fstream)|Type `basic_fstream` spécialisé sur les **`char`** paramètres de modèle.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Type `basic_ifstream` spécialisé sur les **`char`** paramètres de modèle.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Type `basic_ofstream` spécialisé sur les **`char`** paramètres de modèle.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Type `basic_fstream` spécialisé sur les **`wchar_t`** paramètres de modèle.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Type `basic_ifstream` spécialisé sur les **`wchar_t`** paramètres de modèle.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Type `basic_ofstream` spécialisé sur les **`wchar_t`** paramètres de modèle.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Type `basic_filebuf` spécialisé sur les **`wchar_t`** paramètres de modèle.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Le modèle de classe décrit une mémoire tampon de flux qui contrôle la transmission d’éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` , vers et à partir d’une séquence d’éléments stockés dans un fichier externe.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Le modèle de classe décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> , avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` .|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Le modèle de classe décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> , avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` .|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Le modèle de classe décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> , avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` .|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
