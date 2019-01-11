---
title: 'Procédure : Créer et utiliser des Instances weak_ptr'
ms.custom: how-to
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: 1a0e2880e97a77a0c9975553631a6024072745f0
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220320"
---
# <a name="how-to-create-and-use-weakptr-instances"></a>Procédure : Créer et utiliser des Instances weak_ptr

Parfois, un objet doit stocker un moyen d’accéder à l’objet sous-jacent d’un `shared_ptr` sans provoquer le décompte de références à incrémenter. En règle générale, cette situation se produit lorsque vous avez des références cycliques entre `shared_ptr` instances.

La meilleure conception consiste à éviter la propriété partagée de pointeurs, chaque fois que vous pouvez. Toutefois, si vous devez avoir partagé approprier `shared_ptr` instances, évitez les références cycliques entre eux. Lorsque les références cycliques sont inévitables, voire préférables pour une raison quelconque, utilisez `weak_ptr` afin de donner à un ou plusieurs propriétaires une référence faible à un autre `shared_ptr`. En utilisant un `weak_ptr`, vous pouvez créer un `shared_ptr` qui joint à un jeu existant d’instances connexes, mais uniquement si la ressource de mémoire sous-jacente est encore valide. Un `weak_ptr` lui-même ne participe pas au décompte, et par conséquent, il ne peut pas empêcher le décompte de références d’atteindre zéro. Toutefois, vous pouvez utiliser un `weak_ptr` à essayer d’obtenir une nouvelle copie de la `shared_ptr` avec lequel il a été initialisé. Si la mémoire a déjà été supprimée, un `bad_weak_ptr` exception est levée. Si la mémoire est toujours valide, le nouveau pointeur partagé incrémente le décompte de références et garantit que la mémoire sera valide tant que le `shared_ptr` variable reste dans la portée.

## <a name="example"></a>Exemple

L’exemple de code suivant illustre un cas où `weak_ptr` est utilisé pour garantir la suppression appropriée des objets qui ont des dépendances circulaires. Lorsque vous examinez l’exemple, supposons qu’il a été créé uniquement après que les solutions alternatives ont été analysées. Le `Controller` objets représentent certains aspects d’un processus de machine, et elles fonctionnent indépendamment. Chaque contrôleur doit être en mesure d’interroger l’état des autres contrôleurs à tout moment, et chacune d’elles contient une privée `vector<weak_ptr<Controller>>` à cet effet. Chaque vecteur contient une référence circulaire et par conséquent, `weak_ptr` instances sont utilisées au lieu de `shared_ptr`.

[!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]

```Output
Creating Controller0
Creating Controller1
Creating Controller2
Creating Controller3
Creating Controller4
push_back to v[0]: 1
push_back to v[0]: 2
push_back to v[0]: 3
push_back to v[0]: 4
push_back to v[1]: 0
push_back to v[1]: 2
push_back to v[1]: 3
push_back to v[1]: 4
push_back to v[2]: 0
push_back to v[2]: 1
push_back to v[2]: 3
push_back to v[2]: 4
push_back to v[3]: 0
push_back to v[3]: 1
push_back to v[3]: 2
push_back to v[3]: 4
push_back to v[4]: 0
push_back to v[4]: 1
push_back to v[4]: 2
push_back to v[4]: 3
use_count = 1
Status of 1 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = O
nStatus of 1 = On
Status of 2 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 3 = On
Destroying Controller0
Destroying Controller1
Destroying Controller2
Destroying Controller3
Destroying Controller4
Press any key
```

À titre d’expérimentation, remplacez le vecteur `others` soit un `vector<shared_ptr<Controller>>`et dans la sortie, notez qu’aucune destructeurs ne sont appelés lorsque `TestRun` retourne.

## <a name="see-also"></a>Voir aussi

[Pointeurs intelligents (C++ moderne)](../cpp/smart-pointers-modern-cpp.md)
