---
title: collate_byname, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- locale/std::collate_byname
dev_langs:
- C++
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41b5be0df93fcc5fcb1c1c18eddb0b051f1da8a8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="collatebyname-class"></a>collate_byname, classe

Classe de modèle dérivée qui décrit un objet susceptible de servir de facette d'assemblage de paramètres régionaux donnés, permettant ainsi la récupération d'informations spécifiques à une zone culturelle concernant les conventions de tri de chaîne.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>Paramètres

`_Locname` Paramètres régionaux nommée.

`_Refs` Un décompte de références initial.

## <a name="remarks"></a>Notes

Classe de modèle qui décrit un objet pouvant servir de [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class) de type [collate](../standard-library/collate-class.md#collate)\<CharType>. Son comportement est déterminé par les paramètres régionaux [nommés](../standard-library/locale-class.md#name) `_Locname`. Chaque constructeur initialise son objet de base avec [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`).

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
