---
title: '&lt;fstream&gt;, typedefs'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 57e481c131a6e4a1111b1ed88217b891d6fc96a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317194"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt;, typedefs

||||
|-|-|-|
|[filebuf](#filebuf)|[Fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a><a name="filebuf"></a>filebuf

Un `basic_filebuf` type spécialisé sur les paramètres du modèle **de char.**

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_filebuf](../standard-library/basic-filebuf-class.md), spécialisé pour les éléments de type **char** avec des traits de caractère par défaut.

## <a name="fstream"></a><a name="fstream"></a>Fstream

Un `basic_fstream` type spécialisé sur les paramètres du modèle **de char.**

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_fstream](../standard-library/basic-fstream-class.md), spécialisé pour les éléments de type **char** avec des traits de caractère par défaut.

## <a name="ifstream"></a><a name="ifstream"></a>ifstream

Définit un flux à utiliser pour lire les données codées sur un octet de façon séquentielle dans un fichier. `ifstream`est un tapdef qui se `basic_ifstream` spécialise dans le modèle de classe pour **l’omble**chevalier .

Il ya `wifstream`aussi , un tapdef qui se spécialise à lire `basic_ifstream` **wchar_t** caractères à double échelle. Pour plus d’informations, consultez [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_ifstream](../standard-library/basic-ifstream-class.md), spécialisé pour les éléments de type char avec des traits de caractère par défaut. Voici un exemple :

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a>destream

Un `basic_ofstream` type spécialisé sur les paramètres du modèle **de char.**

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_ofstream](../standard-library/basic-ofstream-class.md), spécialisé pour les éléments de type **char** avec des traits de caractère par défaut.

## <a name="wfstream"></a><a name="wfstream"></a>wfstream

Un `basic_fstream` type spécialisé sur **wchar_t** paramètres du modèle.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_fstream](../standard-library/basic-fstream-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="wifstream"></a><a name="wifstream"></a>wifstream (wifstream)

Un `basic_ifstream` type spécialisé sur **wchar_t** paramètres du modèle.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_ifstream](../standard-library/basic-ifstream-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="wofstream"></a><a name="wofstream"></a>wofstream (wofstream)

Un `basic_ofstream` type spécialisé sur **wchar_t** paramètres du modèle.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_ofstream](../standard-library/basic-ofstream-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="wfilebuf"></a><a name="wfilebuf"></a>wfilebuf wfilebuf

Un `basic_filebuf` type spécialisé sur **wchar_t** paramètres du modèle.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Notes

Le type est synonyme de modèle de classe [basic_filebuf](../standard-library/basic-filebuf-class.md), spécialisé pour les éléments de type **wchar_t** avec des traits de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<fstream>](../standard-library/fstream.md)
