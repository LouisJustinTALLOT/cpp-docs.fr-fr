---
title: messages_byname, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmes/std::messages_byname
dev_langs:
- C++
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eab07f19f9d5025eba1ffe82c7e23066683b6267
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852977"
---
# <a name="messagesbyname-class"></a>messages_byname, classe

La classe de modèle dérivée décrit un objet pouvant servir de facette de message de paramètres régionaux donnés, permettant ainsi la récupération de messages localisés.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>Paramètres

`_Locname` Paramètres régionaux nommée.

`_Refs` Un décompte de références initial.

## <a name="remarks"></a>Notes

Son comportement est déterminé par les paramètres régionaux nommés `_Locname`. Chaque constructeur initialise son objet de base avec [messages](../standard-library/messages-class.md#messages)\<CharType>( `_Refs`).

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
