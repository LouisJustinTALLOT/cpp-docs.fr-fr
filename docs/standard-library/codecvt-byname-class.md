---
title: codecvt_byname, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt_byname
dev_langs:
- C++
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0241d88c532fc5f4bff0d8a76a16c5bfe434e22a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="codecvtbyname-class"></a>codecvt_byname, classe
Classe de modèle dérivée qui décrit un objet susceptible de servir de facette d'assemblage de paramètres régionaux donnés, permettant ainsi la récupération d'informations spécifiques à une zone culturelle concernant les conversions.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```  
  
```
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```  
  
```
protected:
    virtual ~codecvt_byname();

};
```  
  
#### <a name="parameters"></a>Paramètres  
 `_Locname`  
 Paramètres régionaux nommés.  
  
 `_Refs`  
 Nombre initial de références.  
  
## <a name="remarks"></a>Notes  
 Les facettes byname sont créées automatiquement pendant la construction de paramètres régionaux nommés.  
  
 Leur comportement est déterminé par les paramètres régionaux nommés `_Locname`. Chaque constructeur initialise son objet de base avec [odecvt](../standard-library/codecvt-class.md)\<CharType, Byte, StateType>( `_Refs`).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** \<locale>  
  
 **Espace de noms :** std  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



