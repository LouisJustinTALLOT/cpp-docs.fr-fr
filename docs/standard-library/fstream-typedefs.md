---
title: '&lt;fstream&gt;, typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 49c5af53c6d174e7f87f75ad8970726c526db714
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962973"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt;, typedefs

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Un type `basic_filebuf` spécialisé sur **char** paramètres de modèle.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_filebuf](../standard-library/basic-filebuf-class.md), spécialisé pour les éléments de type **char** ayant les caractéristiques par défaut.

## <a name="fstream"></a>  fstream

Un type `basic_fstream` spécialisé sur **char** paramètres de modèle.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_fstream](../standard-library/basic-fstream-class.md), spécialisé pour les éléments de type **char** ayant les caractéristiques par défaut.

## <a name="ifstream"></a>  ifstream

Définit un flux à utiliser pour lire les données codées sur un octet de façon séquentielle dans un fichier. `ifstream` est un typedef qui spécialise la classe de modèle `basic_ifstream` pour **char**.

Il existe également `wifstream`, un typedef qui spécialise `basic_ifstream` lire **wchar_t** caractères double largeur. Pour plus d’informations, consultez [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ifstream](../standard-library/basic-ifstream-class.md), spécialisé pour les éléments de type char ayant les caractéristiques par défaut. Voici un exemple :

`using namespace std;`

`ifstream infile("existingtextfile.txt");`

`if (!infile.bad())`

`{`

`// Dump the contents of the file to cout.`

`cout << infile.rdbuf();`

`infile.close();`

`}`

## <a name="ofstream"></a>  ofstream

Un type `basic_ofstream` spécialisé sur **char** paramètres de modèle.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ofstream](../standard-library/basic-ofstream-class.md), spécialisé pour les éléments de type **char** ayant les caractéristiques par défaut.

## <a name="wfstream"></a>  wfstream

Un type `basic_fstream` spécialisé sur **wchar_t** paramètres de modèle.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_fstream](../standard-library/basic-fstream-class.md), spécialisé pour les éléments de type **wchar_t** ayant les caractéristiques par défaut.

## <a name="wifstream"></a>  wifstream

Un type `basic_ifstream` spécialisé sur **wchar_t** paramètres de modèle.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ifstream](../standard-library/basic-ifstream-class.md), spécialisé pour les éléments de type **wchar_t** ayant les caractéristiques par défaut.

## <a name="wofstream"></a>  wofstream

Un type `basic_ofstream` spécialisé sur **wchar_t** paramètres de modèle.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_ofstream](../standard-library/basic-ofstream-class.md), spécialisé pour les éléments de type **wchar_t** ayant les caractéristiques par défaut.

## <a name="wfilebuf"></a>  wfilebuf

Un type `basic_filebuf` spécialisé sur **wchar_t** paramètres de modèle.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la classe de modèle [basic_filebuf](../standard-library/basic-filebuf-class.md), spécialisé pour les éléments de type **wchar_t** ayant les caractéristiques par défaut.

## <a name="see-also"></a>Voir aussi

[\<fstream>](../standard-library/fstream.md)<br/>
