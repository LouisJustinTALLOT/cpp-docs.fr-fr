---
title: /Zc:alignedNew (c ++ 17 trop d’allocation alignée) | Documents Microsoft
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:alignedNew
dev_langs:
- C++
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
author: corob-msft
ms.author: corob
ms.openlocfilehash: 5f9527d63a9843bd4df90520e5b4759126d72fe1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378383"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (c ++ 17 trop d’allocation alignée)

Activer la prise en charge pour C ++ 17 trop forte aligné **nouveau**, allocation de mémoire dynamique alignée sur les limites supérieures à la valeur par défaut pour la taille maximale aligné type standard, **max\_aligner\_t**.

## <a name="syntax"></a>Syntaxe

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>Notes

Visual Studio version 15.5 permet de compilateur et la prise en charge de la bibliothèque C ++ 17 standard alignés de manière excessive dynamique d’allocation de mémoire. Lorsque le **/Zc:alignedNew** option est spécifiée, une allocation dynamique comme `new Example;` respecte l’alignement de *exemple* même quand il est supérieur à `max_align_t`, le plus grand alignement obligatoire pour tous les types fondamentaux. Lorsque l’alignement du type alloué n’est pas plus d’assuré par l’opérateur d’origine **nouveau**, disponible en tant que la valeur de la macro prédéfinie  **\_ \_STDCPP\_par défaut \_Nouveau\_alignement\_\_**, l’instruction `new Example;` entraîne un appel à `::operator new(size_t)` comme dans C ++ 14. Lorsque l’alignement est supérieur à  **\_ \_STDCPP\_par défaut\_nouveau\_alignement\_\_**, l’implémentation obtient à la place la mémoire à l’aide de `::operator new(size_t, align_val_t)`. De même, la suppression de types alignés de manière excessive appelle `::operator delete(void*, align_val_t)` ou la taille supprimer la signature `::operator delete(void*, size_t, align_val_t)`.

Le **/Zc:alignedNew** option est disponible uniquement lorsque [/std : c ++ 17](std-specify-language-standard-version.md) ou [/std : c ++ dernière](std-specify-language-standard-version.md) est activé. Sous **/std : c ++ 17** ou **/std : c ++ dernière**, **/Zc:alignedNew** est activée par défaut pour se conformer à la norme ISO C ++ 17 standard. Si la seule raison vous implémenter l’opérateur **nouveau** et **supprimer** doit prendre en charge les allocations alignées de manière excessive, vous devrez peut-être ne sont plus ce code dans le mode C ++ 17. Pour désactiver cette option et rétablir le comportement 14 C ++ de **nouveau** et **supprimer** lorsque **/std::c ++ 17** ou **/std : c ++ dernière** est spécifié, Spécifiez **/Zc:alignedNew-**. Si vous implémentez l’opérateur **nouveau** et **supprimer** , mais vous n’êtes pas prêt à implémenter l’opérateur aligné de manière excessive **nouveau** et **supprimer** surcharges ayant le `align_val_t` paramètre, utilisez le **/Zc:alignedNew-** option pour empêcher le compilateur et la bibliothèque Standard à partir de la génération d’appels aux surcharges alignés de manière excessive. Le [/ permissive-](permissive-standards-conformance.md) option ne modifie pas le paramètre par défaut de **/Zc:alignedNew**.

## <a name="example"></a>Exemple

Cet exemple montre comment opérateur **nouveau** et opérateur **supprimer** comporte quand le **/Zc:alignedNew** option est définie.

```cpp
// alignedNew.cpp
// Compile by using: cl /EHsc /std:c++17 /W4 alignedNew.cpp
#include <iostream>
#include <malloc.h>
#include <new>

// "old" unaligned overloads
void* operator new(std::size_t size) {
    auto ptr = malloc(size);
    std::cout << "unaligned new(" << size << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size) {
    std::cout << "unaligned sized delete(" << ptr << ", " << size << ")\n";
    free(ptr);
}

void operator delete(void* ptr) {
    std::cout << "unaligned unsized delete(" << ptr << ")\n";
    free(ptr);
}

// "new" over-aligned overloads
void* operator new(std::size_t size, std::align_val_t align) {
    auto ptr = _aligned_malloc(size, static_cast<std::size_t>(align));
    std::cout << "aligned new(" << size << ", " <<
        static_cast<std::size_t>(align) << ") = " << ptr << '\n';
    return ptr ? ptr : throw std::bad_alloc{};
}

void operator delete(void* ptr, std::size_t size, std::align_val_t align) {
    std::cout << "aligned sized delete(" << ptr << ", " << size << 
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

void operator delete(void* ptr, std::align_val_t align) {
    std::cout << "aligned unsized delete(" << ptr << 
        ", " << static_cast<std::size_t>(align) << ")\n";
    _aligned_free(ptr);
}

struct alignas(256) OverAligned {}; // warning C4324, structure is padded

int main() {
    delete new int;
    delete new OverAligned;
}
```

Cette sortie est courant pour les versions 32 bits. Le pointeur de valeurs différentes selon lequel votre application s’exécute dans la mémoire.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier la **des Options supplémentaires** propriété à inclure **/Zc:alignedNew** ou **/Zc:alignedNew-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)  
