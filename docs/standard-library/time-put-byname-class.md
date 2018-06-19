---
title: time_put_byname, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xloctime/std::time_put_byname
dev_langs:
- C++
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39db2ead78a123c3274405e3560bca1c67cf1f5c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854140"
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

`_Locname` Un nom de paramètres régionaux.

`_Refs` Un décompte de références initial.

## <a name="remarks"></a>Notes

Son comportement est déterminé par les paramètres régionaux [nommés](../standard-library/locale-class.md#name) `_Locname`. Chaque constructeur initialise son objet de base avec [time_put](../standard-library/time-put-class.md#time_put)\<CharType, OutputIterator>( `_Refs`).

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
