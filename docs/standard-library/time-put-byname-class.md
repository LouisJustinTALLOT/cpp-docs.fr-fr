---
title: time_put_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: ffe7aa276e9380b6544a78c1c1735ab57765507a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495964"
---
# <a name="timeputbyname-class"></a>time_put_byname, classe

La classe de modèle dérivée décrit un objet pouvant servir de facette de paramètres régionaux du type `time_put`\< CharType, OutputIterator >.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>Paramètres

*_Locname*<br/>
Nom de paramètres régionaux.

*_Refs*<br/>
Nombre initial de références.

## <a name="remarks"></a>Notes

Son comportement est déterminé par le [nommé](../standard-library/locale-class.md#name) paramètres régionaux *_Locname*. Chaque constructeur initialise son objet de base avec [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator > (`_Refs`).

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
