---
title: 'Procédure : Créer et utiliser des instances weak_ptr'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: d7caea7cfd13b3a41a1cd20f88a9914267cf9677
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187853"
---
# <a name="how-to-create-and-use-weak_ptr-instances"></a>Procédure : Créer et utiliser des instances weak_ptr

Parfois, un objet doit stocker un moyen d’accéder à l’objet sous-jacent d’un [shared_ptr](../standard-library/shared-ptr-class.md) sans entraîner l’incrémentation du décompte de références. En général, cette situation se produit lorsque vous avez des références cycliques entre des `shared_ptr` instances.

La meilleure conception consiste à éviter la propriété partagée des pointeurs chaque fois que vous le pouvez. Toutefois, si vous devez disposer d’une propriété partagée d' `shared_ptr` instances, évitez les références cycliques entre elles. Lorsque les références cycliques sont inévitables, voire préférables pour une raison quelconque, utilisez [weak_ptr](../standard-library/weak-ptr-class.md) pour attribuer à un ou plusieurs propriétaires une référence faible à une autre `shared_ptr` . À l’aide d’un `weak_ptr` , vous pouvez créer un `shared_ptr` qui se joint à un ensemble existant d’instances associées, mais uniquement si la ressource de mémoire sous-jacente est toujours valide. Un `weak_ptr` lui-même ne participe pas au décompte de références et, par conséquent, il ne peut pas empêcher le décompte de références de passer à zéro. Toutefois, vous pouvez utiliser un `weak_ptr` pour essayer d’obtenir une nouvelle copie de `shared_ptr` avec laquelle il a été initialisé. Si la mémoire a déjà été supprimée, l' `weak_ptr` opérateur bool de est retourné **`false`** . Si la mémoire est toujours valide, le nouveau pointeur partagé incrémente le décompte de références et garantit que la mémoire sera valide tant que la `shared_ptr` variable reste dans la portée.

## <a name="example"></a>Exemple

L’exemple de code suivant montre un cas dans lequel `weak_ptr` est utilisé pour garantir la suppression correcte des objets qui ont des dépendances circulaires. Lorsque vous examinez l’exemple, supposons qu’il a été créé uniquement après la prise en compte de solutions alternatives. Les `Controller` objets représentent un aspect d’un processus d’ordinateur et ils fonctionnent de manière indépendante. Chaque contrôleur doit être en mesure d’interroger l’état des autres contrôleurs à tout moment, et chacun d’eux contient un privé à `vector<weak_ptr<Controller>>` cet effet. Chaque vecteur contient une référence circulaire et, par conséquent, les `weak_ptr` instances sont utilisées à la place de `shared_ptr` .

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
Status of 0 = On
Status of 1 = On
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

En guise d’expérience, modifiez le vecteur pour qu’il `others` soit un `vector<shared_ptr<Controller>>` , puis dans la sortie, Notez qu’aucun destructeur n’est appelé quand `TestRun` retourne.

## <a name="see-also"></a>Voir aussi

[Pointeurs intelligents (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
