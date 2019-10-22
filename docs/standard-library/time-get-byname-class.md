---
title: time_get_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: 9df3831e085f1dea1df45ff9368479fa516b944e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685755"
---
# <a name="time_get_byname-class"></a>time_get_byname, classe

Le modèle de classe dérivée décrit un objet pouvant servir de facette de paramètres régionaux de type `time_get` \<CharType, InputIterator >.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```

### <a name="parameters"></a>Paramètres

*_Locname* \
Paramètres régionaux nommés.

*_Refs* \
Nombre initial de références.

## <a name="requirements"></a>spécifications

Son comportement est déterminé par les paramètres régionaux nommés *_Locname*. Chaque constructeur initialise son objet de base avec [time_get](../standard-library/time-get-class.md#time_get)\<CharType, InputIterator>( `_Refs`).

## <a name="requirements"></a>spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
