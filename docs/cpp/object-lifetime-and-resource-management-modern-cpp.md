---
title: Objet de durée de vie et de gestion des ressources (Modern C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 365f9196f3d482098c29bf4b04610120ecbbeec4
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406040"
---
# <a name="object-lifetime-and-resource-management-modern-c"></a>Gestion de la durée de vie et des ressources de l'objet (Modern C++)
Contrairement aux langages managés, C++ ne possède aucun garbage collection (GC), ce qui libère automatiquement les ressources mémoire qui ne sont plus utilisées lors de l’exécution d’un programme. En C++, la gestion des ressources est directement liée à la durée de vie des objets. Ce document explique les facteurs qui affectent la durée de vie des objets en C++ et leur mode de gestion.  
  
 C++ ne comporte pas de garbage collection (GC), essentiellement parce qu'il ne gère pas les ressources non liées à la mémoire. Seuls les destructeurs déterministes comme ceux en C++ peuvent gérer de manière identique les ressources mémoire et non-mémoire. Le GC présente également d'autres problèmes, comme une surcharge plus élevée de la mémoire et une consommation de processeur, ainsi que la localité. Mais l'universalité est un problème fondamental qui ne peut pas être atténué via des optimisations intelligentes.  
  
## <a name="concepts"></a>Concepts  
 Un point essentiel de la gestion de la durée de vie des objets est l'encapsulation - la valeur à l'objet n'a pas besoin de connaître les ressources que possède l'objet, ou comment les supprimer à partir de celles-ci, ou même s'il possède la moindre ressource. Elle doit simplement détruire l’objet. Le langage principal C++ est conçu pour vous assurer que les objets sont détruits aux moments appropriés, autrement dit, lorsque les blocs sont fermés, dans l'ordre inverse de la construction. Lorsqu'un objet est détruit, ses bases et membres sont détruits dans un ordre précis.  Le langage détruit automatiquement les objets, à moins que vous ne fassiez des opérations particulières telles que l’allocation de tas ou un nouveau positionnement.  Par exemple, [intelligente des pointeurs](../cpp/smart-pointers-modern-cpp.md) comme `unique_ptr` et `shared_ptr`, et les conteneurs de bibliothèque Standard C++ comme `vector`, encapsuler **nouveau** /  **supprimer** et `new[]` / `delete[]` dans des objets, qui ont des destructeurs. C’est pourquoi il est donc important d’utiliser des pointeurs intelligents et les conteneurs de bibliothèque C++ Standard.  
  
 Un autre concept important dans la gestion de la durée de vie : les destructeurs. Les destructeurs encapsulent la mise en production de la ressource.  (La mnémonique utilisée couramment est RRID, Resource Release Is Destruction.)  Une ressource est un élément que vous obtenez du "système" et que vous devez rendre plus ultérieurement.  La mémoire est la ressource la plus courante, mais il existe également des fichiers, des sockets, des textures et d'autres ressources non liées à la mémoire. Être "propriétaire" d'une ressource signifie que vous pouvez l'utiliser en cas de besoin, mais que vous devez également la libérer lorsque vous avez fini de l'utiliser.  Lorsqu’un objet est détruit, le destructeur libère les ressources dont il était propriétaire.  
  
 Le concept final est le DAG (Directed Acyclic Graph).  La structure de la propriété dans un programme forme un DAG. Aucun objet ne peut se posséder lui-même, c'est non seulement impossible mais cela n'a aucun sens. En revanche, deux objets peuvent partager la propriété d'un troisième objet.  Plusieurs types de liens sont possibles dans un DAG comme suit : A est un membre de B (B possède A), C stocke `vector<D>` (C possède chaque élément de D), E stocke `shared_ptr<F>` (E partage la propriété de F, éventuellement d'autres objets), etc.  Tant qu'il n'y a pas de cycles et que chaque lien dans le DAG est représenté par un objet qui possède un destructeur (au lieu d'un pointeur brut, d'un handle ou de tout autre mécanisme), d'éventuelles fuites de ressources sont impossibles car le langage les évite. Les ressources sont libérées dès qu’elles ne sont plus nécessaires, sans exécution du garbage collector. Le suivi de la durée de vie est sans surcharge pour la place de pile, les bases, les membres, les cas associés, et peu coûteuse pour `shared_ptr`.  
  
### <a name="heap-based-lifetime"></a>Durée de vie basée sur un tas  
 Pour la durée de vie d’objet du tas, utilisez [intelligente des pointeurs](../cpp/smart-pointers-modern-cpp.md). Utilisez `shared_ptr` et `make_shared` en tant que pointeur et allocateur par défaut. Utilisez `weak_ptr` pour désactiver des cycles, effectuer la mise en cache et observer des objets sans affecter ni présumer quoique ce soit sur leurs durées de vie.  
  
```cpp  
void func() {  
  
auto p = make_shared<widget>(); // no leak, and exception safe  
...  
p->draw();   
  
} // no delete required, out-of-scope triggers smart pointer destructor  
```  
  
 Utilisez `unique_ptr` pour une propriété unique, par exemple, dans le *pimpl* idiome. (Consultez [Pimpl pour l’Encapsulation de compilation](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md).) Rendre un `unique_ptr` la cible principale de tous explicites **nouveau** expressions.  
  
```cpp  
unique_ptr<widget> p(new widget());  
```  
  
 Vous pouvez utiliser des pointeurs bruts pour une absence de propriété et une observation. Un pointeur non propriétaire peut "se balancer", mais il ne peut pas fuir.  
  
```cpp  
class node {  
  ...  
  vector<unique_ptr<node>> children; // node owns children  
  node* parent; // node observes parent, which is not a concern  
  ...  
};  
node::node() : parent(...) { children.emplace_back(new node(...) ); }  
```  
  
 Lorsque l’optimisation des performances est requise, vous devrez peut-être utiliser *bien encapsulé* qui possède des pointeurs et des appels explicites à supprimer. L'implémentation de votre propre structure de données de bas niveau en est la parfaite illustration.  
  
### <a name="stack-based-lifetime"></a>Durée de vie basée sur la pile  
 En C++ moderne, *étendue basée sur pile* constitue un moyen efficace pour écrire du code fiable car elle combine automatique *durée de vie de pile* et *durée de vie de données membre* avec une grande efficacité : durée de vie de suivi est essentiellement sans surcharge. La durée de vie de l'objet heap requiert une gestion manuelle diligente et peut être la source de fuites et d'inefficacités des ressources, surtout si vous utilisez des pointeurs bruts. Tenez compte de ce code qui illustre la portée basée sur la pile :  
  
```cpp  
class widget {  
private:  
    gadget g;   // lifetime automatically tied to enclosing object  
public:  
    void draw();  
};  
  
void functionUsingWidget () {  
    widget w;   // lifetime automatically tied to enclosing scope  
                // constructs w, including the w.g gadget member  
    // ...
    w.draw();  
    // ...
} // automatic destruction and deallocation for w and w.g  
  // automatic exception safety,   
  // as if "finally { w.dispose(); w.g.dispose(); }"  
```  
  
 Utilisez la durée de vie statique avec parcimonie (statique globale, fonction statique locale) car des problèmes peuvent survenir. Que se produit-il lorsque le constructeur d'un objet global lève une exception ? En général, l'application échoue d'une manière qui rend le débogage difficile. L'ordre de construction pose problème pour les objets de durée de vie statique, et n'est pas sécurisé vis à vis de la concurrence. Non seulement la construction d'un objet constitue un problème, mais l'ordre de destruction peut être complexe, surtout lorsque le polymorphisme est implicite. Même si votre objet ou variable n'est pas polymorphe et n'a pas de classement de construction ou de destruction complexes, il y a toujours la question de la sécurité du thread vis à vis de la concurrence. Une application multithread ne peut pas modifier sans risque les données des objets statiques sans avoir un stockage local des threads, des verrous de ressources, ainsi que des précautions spéciales.  
  
## <a name="see-also"></a>Voir aussi  
 [Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)   
 [Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)