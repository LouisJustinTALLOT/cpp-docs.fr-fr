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
ms.openlocfilehash: 3f4104b28f5becfdbf62ede16faa81e855fcac8c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421778"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt;, typedefs

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Type `basic_filebuf` spécialisé sur les paramètres de modèle **char** .

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_filebuf](../standard-library/basic-filebuf-class.md), spécialisé pour les éléments de type **char** avec des caractéristiques de caractère par défaut.

## <a name="fstream"></a>  fstream

Type `basic_fstream` spécialisé sur les paramètres de modèle **char** .

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_fstream](../standard-library/basic-fstream-class.md), spécialisé pour les éléments de type **char** avec des caractéristiques de caractère par défaut.

## <a name="ifstream"></a>  ifstream

Définit un flux à utiliser pour lire les données codées sur un octet de façon séquentielle dans un fichier. `ifstream` est un typedef qui spécialise le modèle de classe `basic_ifstream` pour **char**.

Il existe également `wifstream`, un typedef qui spécialise `basic_ifstream` lire **wchar_t** caractères à double larges. Pour plus d’informations, consultez [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_ifstream](../standard-library/basic-ifstream-class.md), spécialisé pour les éléments de type char avec des caractéristiques de caractère par défaut. Voici un exemple :

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>  ofstream

Type `basic_ofstream` spécialisé sur les paramètres de modèle **char** .

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_ofstream](../standard-library/basic-ofstream-class.md), spécialisé pour les éléments de type **char** avec des caractéristiques de caractère par défaut.

## <a name="wfstream"></a>  wfstream

Type `basic_fstream` spécialisé sur les paramètres de modèle de **wchar_t** .

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_fstream](../standard-library/basic-fstream-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="wifstream"></a>  wifstream

Type `basic_ifstream` spécialisé sur les paramètres de modèle de **wchar_t** .

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_ifstream](../standard-library/basic-ifstream-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="wofstream"></a>  wofstream

Type `basic_ofstream` spécialisé sur les paramètres de modèle de **wchar_t** .

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_ofstream](../standard-library/basic-ofstream-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="wfilebuf"></a>  wfilebuf

Type `basic_filebuf` spécialisé sur les paramètres de modèle de **wchar_t** .

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du modèle de classe [basic_filebuf](../standard-library/basic-filebuf-class.md), spécialisé pour les éléments de type **wchar_t** avec des caractéristiques de caractère par défaut.

## <a name="see-also"></a>Voir aussi

[\<fstream>](../standard-library/fstream.md)
