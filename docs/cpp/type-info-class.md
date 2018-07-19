---
title: type_info, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- type_info
dev_langs:
- C++
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54e4f4a2ac9be9dc68320e5121bc86e5a4280807
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941039"
---
# <a name="typeinfo-class"></a>type_info, classe
Le `type_info` classe décrit les informations de type générées dans le programme par le compilateur. Les objets de cette classe stockent efficacement un pointeur dans un nom pour le type. Le `type_info` classe stocke également une valeur encodée appropriée pour comparer deux types d’égalité ou l’ordre de classement. Les règles d'encodage et la séquence de classement pour les types ne sont pas spécifiées et peuvent différer entre les programmes.  
  
 Le `<typeinfo>` fichier d’en-tête doit être inclus afin d’utiliser la `type_info` classe. L’interface pour la `type_info` classe est :  
  
```cpp
class type_info {  
public:  
    virtual ~type_info();  
    size_t hash_code() const  
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;  
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;  
    _CRTIMP_PURE int before(const type_info& rhs) const;  
    _CRTIMP_PURE const char* name() const;  
    _CRTIMP_PURE const char* raw_name() const;  
};  
```  
  
 Vous ne pouvez pas instancier des objets de la `type_info` classe directement, car la classe a uniquement un constructeur de copie privé. La seule façon de construire un (temporaire) `type_info` objet consiste à utiliser le [typeid](../cpp/typeid-operator.md) opérateur. Dans la mesure où l’opérateur d’assignation est également privé, Impossible de copier ou assigner des objets de classe `type_info`.  
  
 `type_info::hash_code` définit une fonction de hachage appropriée pour mapper des valeurs de type `typeinfo` pour une distribution de valeurs d’index.  
  
 Les opérateurs `==` et `!=` peut être utilisé pour comparer l’égalité et inégalité avec d’autres `type_info` des objets, respectivement.  
  
 Il n'existe aucun lien entre l'ordre de classement des types et les relations d'héritage. Utilisez le `type_info::before` fonction membre pour déterminer l’ordre de tri des types. Il n’existe aucune garantie que `type_info::before` génère le même résultat dans des programmes différents ou même différentes exécutions du même programme. De cette manière, `type_info::before` est similaire à l’adresse de `(&)` opérateur.  
  
 Le `type_info::name` fonction membre retourne un `const char*` vers une chaîne se terminant par null qui représente le nom explicite du type. La mémoire désignée est mise en cache et ne doit jamais être directement libérée.  
  
 Le `type_info::raw_name` fonction membre retourne un `const char*` vers une chaîne se terminant par null qui représente le nom décoré du type d’objet. Le nom est réellement stocké sous sa forme décorée pour économiser de l'espace. Par conséquent, cette fonction est plus rapide que `type_info::name` , car il n’a pas besoin de décoration de nom. La chaîne retournée par la `type_info::raw_name` fonction est utile dans les opérations de comparaison mais n’est pas lisible. Si vous avez besoin d’une chaîne, lisible, utilisez le `type_info::name` fonctionner à la place.  
  
 Informations de type sont générées pour les classes polymorphes uniquement si le [/GR (activer les informations de Type au moment de l’exécution)](../build/reference/gr-enable-run-time-type-information.md) option du compilateur est spécifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de type au moment de l’exécution](../cpp/run-time-type-information.md)
