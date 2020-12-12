---
description: 'En savoir plus sur : classe moneypunct_byname'
title: moneypunct_byname, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct_byname
helpviewer_keywords:
- moneypunct_byname class
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
ms.openlocfilehash: b20293ac6788156f25f95878a5ab0098c178edec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277464"
---
# <a name="moneypunct_byname-class"></a>moneypunct_byname, classe

Modèle de classe dérivée qui décrit un objet pouvant servir de `moneypunct` facette de paramètres régionaux donnés, permettant ainsi de mettre en forme le champ d’entrée monétaire ou les champs de sortie monétaire.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, bool Intl = false>
class moneypunct_byname : public moneypunct<CharType, Intl>
{
public:
    explicit moneypunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit moneypunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~moneypunct_byname();

};
```

## <a name="remarks"></a>Notes

Son comportement est déterminé par les paramètres régionaux nommés `_Locname`. Chaque constructeur initialise son objet de base avec [moneypunct](../standard-library/moneypunct-class.md#moneypunct) \<CharType, Intl> ( `_Refs` ).

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
