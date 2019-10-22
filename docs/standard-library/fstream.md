---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 1f85367b9ae527c9387d085acc1496bfbbf7cc9e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688035"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

Définit plusieurs classes qui prennent en charge les opérations iostreams sur des séquences stockées dans des fichiers externes.

## <a name="syntax"></a>Syntaxe

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Type `basic_filebuf` spécialisé sur les paramètres de modèle **char** .|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Type `basic_fstream` spécialisé sur les paramètres de modèle **char** .|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Type `basic_ifstream` spécialisé sur les paramètres de modèle **char** .|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Type `basic_ofstream` spécialisé sur les paramètres de modèle **char** .|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Type `basic_fstream` spécialisé sur les paramètres de modèle **wchar_t** .|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Type `basic_ifstream` spécialisé sur les paramètres de modèle **wchar_t** .|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Type `basic_ofstream` spécialisé sur les paramètres de modèle **wchar_t** .|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Type `basic_filebuf` spécialisé sur les paramètres de modèle **wchar_t** .|

### <a name="classes"></a>Classes

|Class|Description|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|Le modèle de classe décrit une mémoire tampon de flux qui contrôle la transmission d’éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Tr`, vers et à partir d’une séquence d’éléments stockés dans un fichier externe.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|Le modèle de classe décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, avec des éléments de type `Elem`, dont le caractère les caractéristiques sont déterminées par la classe `Tr`.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|Le modèle de classe décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, avec des éléments de type `Elem`, dont les caractéristiques sont déterminé par la classe `Tr`.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|Le modèle de classe décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **TR**>, avec des éléments de type `Elem`, dont les caractéristiques sont déterminées. par la classe `Tr`.|

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
