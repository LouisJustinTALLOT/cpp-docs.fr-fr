---
title: '&lt;fstream&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <fstream>
dev_langs:
- C++
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d2fa3ef6113add6bcf72f85f74b8722033cb8d5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846608"
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
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|Type `basic_filebuf` spécialisé sur des paramètres de modèle `char`.|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|Type `basic_fstream` spécialisé sur des paramètres de modèle `char`.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|Type `basic_ifstream` spécialisé sur des paramètres de modèle `char`.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|Type `basic_ofstream` spécialisé sur des paramètres de modèle `char`.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|Type `basic_fstream` spécialisé sur des paramètres de modèle `wchar_t`.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|Type `basic_ifstream` spécialisé sur des paramètres de modèle `wchar_t`.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|Type `basic_ofstream` spécialisé sur des paramètres de modèle `wchar_t`.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|Type `basic_filebuf` spécialisé sur des paramètres de modèle `wchar_t`.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|La classe de modèle décrit une mémoire tampon de flux qui contrôle la transmission d’éléments de type **Elem**, dont les caractéristiques sont déterminées par la classe **Tr**, vers et à partir d’une séquence d’éléments stockés dans un fichier externe.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|La classe de modèle décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets codés à l’aide d’une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, avec des éléments de type **Elem**, dont les caractéristiques sont déterminées par la classe **Tr**.|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|La classe de modèle décrit un objet qui contrôle l’extraction d’éléments et d’objets codés à partir d’une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, avec des éléments de type **Elem**, dont les caractéristiques sont déterminées par la classe **Tr**.|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|La classe de modèle décrit un objet qui contrôle l’insertion d’éléments et d’objets codés dans une mémoire tampon de flux de classe [basic_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**>, avec des éléments de type **Elem**, dont les caractéristiques sont déterminées par la classe **Tr**.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
