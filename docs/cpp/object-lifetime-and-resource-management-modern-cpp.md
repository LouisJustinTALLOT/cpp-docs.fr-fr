---
title: Gestion des ressources et de la durée de vie des objets (RAII)
description: Suivez le principe de RAII dans moderne C++ pour éviter les fuites de ressources.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: 01867ec0a71ba54bb6534da1b408cb0610d652a7
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303366"
---
# <a name="object-lifetime-and-resource-management-raii"></a>Gestion des ressources et de la durée de vie des objets (RAII)

Contrairement aux langages C++ managés, n’a pas de *garbage collection*automatique. Il s’agit d’un processus interne qui libère de la mémoire du tas et d’autres ressources au cours de l’exécution d’un programme. Un C++ programme est chargé de retourner toutes les ressources acquises au système d’exploitation. L’échec de la libération d’une ressource inutilisée est appelé une *fuite*. Les ressources divulguées ne sont pas disponibles pour les autres programmes jusqu’à ce que le processus se termine. En particulier, les fuites de mémoire sont une cause courante de bogues dans la programmation de style C.

Moderne C++ évite d’utiliser le tas de mémoire autant que possible en déclarant des objets sur la pile. Quand une ressource est trop volumineuse pour la pile, elle doit être *détenue* par un objet. À mesure que l’objet est initialisé, il acquiert la ressource qu’il possède. L’objet est ensuite chargé de libérer la ressource dans son destructeur. L’objet propriétaire lui-même est déclaré sur la pile. Le principe des *ressources propres aux objets* est également appelé « acquisition des ressources », ou RAII.

Lorsqu’un objet de pile propriétaire de ressources est hors de portée, son destructeur est automatiquement appelé. De cette façon, garbage collection dans C++ est étroitement lié à la durée de vie des objets, et est déterministe. Une ressource est toujours libérée à un point connu du programme, que vous pouvez contrôler. Seuls les destructeurs déterministes comme ceux en C++ peuvent gérer de manière identique les ressources mémoire et non-mémoire.

L’exemple suivant montre un objet simple `w`. Elle est déclarée sur la pile au niveau de la portée de la fonction et est détruite à la fin du bloc de la fonction. L’objet `w` ne possède aucune *ressource* (par exemple, la mémoire allouée par le tas). Son seul `g` membre est déclaré sur la pile et est simplement hors de portée avec `w`. Aucun code spécial n’est nécessaire dans le destructeur `widget`.

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

Dans l’exemple suivant, `w` possède une ressource mémoire et doit donc avoir du code dans son destructeur pour supprimer la mémoire.
 
```cpp
class widget
{
private:
    int* data;
public:
    widget(const int size) { data = new int[size]; } // acquire
    ~widget() { delete[] data; } // release
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                        // constructs w, including the w.data member
    w.do_something();

} // automatic destruction and deallocation for w and w.data

```

Depuis C++ 11, il existe un meilleur moyen d’écrire l’exemple précédent : en utilisant un pointeur intelligent de la bibliothèque standard. Le pointeur intelligent gère l’allocation et la suppression de la mémoire qu’il détient. L’utilisation d’un pointeur intelligent élimine la nécessité d’avoir un destructeur explicite dans la classe `widget`.

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

En utilisant des pointeurs intelligents pour l’allocation de mémoire, vous pouvez éliminer le risque de fuites de mémoire. Ce modèle fonctionne pour d’autres ressources, telles que les descripteurs de fichiers ou les sockets. Vous pouvez gérer vos propres ressources de la même façon dans vos classes. Pour plus d’informations, consultez [pointeurs intelligents](smart-pointers-modern-cpp.md).

La conception de C++ garantit que les objets sont détruits lorsqu’ils sont hors de portée. Autrement dit, elles sont détruites à mesure que des blocs sont quittés, dans l’ordre inverse de la construction. Lorsqu’un objet est détruit, ses bases et membres sont détruits dans un ordre précis. Les objets déclarés en dehors de tout bloc, au niveau de la portée globale, peuvent entraîner des problèmes. Il peut être difficile à déboguer si le constructeur d’un objet global lève une exception.

## <a name="see-also"></a>Voir aussi

[Bienvenue dansC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Référence du langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
