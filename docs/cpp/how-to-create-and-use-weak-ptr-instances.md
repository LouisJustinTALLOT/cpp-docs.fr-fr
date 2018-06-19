---
title: 'Comment : créer et utiliser des Instances weak_ptr | Documents Microsoft'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8fbbf9d3b427c2451fafe0fae93a531dfd45ad8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415143"
---
# <a name="how-to-create-and-use-weakptr-instances"></a>Comment : créer et utiliser des instances weak_ptr
Parfois, un objet doit stocker un moyen d’accéder à l’objet sous-jacent d’un `shared_ptr` sans provoquer le décompte de références à incrémenter. En règle générale, cette situation se produit lorsque vous avez des références cycliques entre `shared_ptr` instances.  
  
 La meilleure conception consiste à éviter les propriété partagée de pointeurs autant que possible. Toutefois, si vous devez avoir partagé approprier `shared_ptr` instances, évitez les références cycliques entre eux. Lorsque des références cycliques sont inévitables, ou même préférable pour une raison quelconque, utilisez `weak_ptr` pour permettre à un ou plusieurs des propriétaires une référence faible à un autre `shared_ptr`. En utilisant un `weak_ptr`, vous pouvez créer un `shared_ptr` qui joint à un ensemble existant d’instances liées, mais uniquement si la ressource mémoire sous-jacente est toujours valide. A `weak_ptr` lui-même ne participe pas le décompte de références, et par conséquent, il ne peut pas empêcher le décompte de références accédant à zéro. Toutefois, vous pouvez utiliser un `weak_ptr` pour essayer d’obtenir une nouvelle copie de la `shared_ptr` avec lequel il a été initialisé. Si la mémoire a déjà été supprimée, un **bad_weak_ptr** exception est levée. Si la mémoire est toujours valide, le nouveau pointeur partagé incrémente le décompte de références et garantit que la mémoire sera valide tant que le `shared_ptr` variable reste dans la portée.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre un cas où `weak_ptr` est utilisé pour garantir la suppression correcte des objets qui ont des dépendances circulaires. Lorsque vous examinez l’exemple, supposons qu’il a été créé uniquement après que les solutions alternatives ont été analysées. Le `Controller` objets représentent certains aspects d’un processus de l’ordinateur, et elles fonctionnent indépendamment. Chaque contrôleur doit être en mesure d’interroger l’état des autres contrôleurs à tout moment, et chacune d’elles contient privé `vector<weak_ptr<Controller>>` à cet effet. Chaque vecteur contient une référence circulaire et par conséquent, `weak_ptr` les instances sont utilisées à la place de `shared_ptr`.  
  
 [!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]  
  
```Output  
Creating Controller0Creating Controller1Creating Controller2Creating Controller3Creating Controller4push_back to v[0]: 1push_back to v[0]: 2push_back to v[0]: 3push_back to v[0]: 4push_back to v[1]: 0push_back to v[1]: 2push_back to v[1]: 3push_back to v[1]: 4push_back to v[2]: 0push_back to v[2]: 1push_back to v[2]: 3push_back to v[2]: 4push_back to v[3]: 0push_back to v[3]: 1push_back to v[3]: 2push_back to v[3]: 4push_back to v[4]: 0push_back to v[4]: 1push_back to v[4]: 2push_back to v[4]: 3use_count = 1Status of 1 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 2 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 3 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 4 = Onuse_count = 1Status of 0 = OnStatus of 1 = OnStatus of 2 = OnStatus of 3 = OnDestroying Controller0Destroying Controller1Destroying Controller2Destroying Controller3Destroying Controller4Press any key  
```  
  
 L’expérience, modifiez le vecteur `others` soit un `vector<shared_ptr<Controller>>`et dans la sortie, notez qu’aucune destructeurs ne sont appelés lorsque `TestRun` renvoie.  
  
## <a name="see-also"></a>Voir aussi  
 [Pointeurs intelligents](../cpp/smart-pointers-modern-cpp.md)