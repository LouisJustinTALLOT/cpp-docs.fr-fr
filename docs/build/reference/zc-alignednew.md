---
title: /Zc:alignedNew (allocation de types suralignés C++17)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: f036c2d7bc4619685d2763702f447476e8e1a1e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217192"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (allocation de types suralignés C++17)

Activer la prise en charge de l’allocation de mémoire dynamique C++ 17 sur-alignée **`new`** alignée sur les limites supérieures à la valeur par défaut pour le type aligné standard de taille maximale, ** \_ alignement \_ Max**.

## <a name="syntax"></a>Syntaxe

> **/Zc : alignedNew** \[ -]

## <a name="remarks"></a>Notes

La bibliothèque et le compilateur MSVC prennent en charge l’allocation de mémoire dynamique suralignée standard C++17. Lorsque l’option **/Zc : alignedNew** est spécifiée, une allocation dynamique telle que `new Example;` respecte l’alignement de l' *exemple* , même lorsqu’il est supérieur à `max_align_t` , le plus grand alignement requis pour tout type fondamental. Lorsque l’alignement du type alloué n’est pas supérieur à l’alignement garanti par l’opérateur d’origine **`new`** , disponible en tant que valeur de la macro prédéfinie ** \_ \_ STDCPP \_ \_ nouvel \_ alignement \_ \_ par défaut**, l’instruction `new Example;` entraîne un appel à `::operator new(size_t)` comme c’était le cas dans c++ 14. Lorsque l’alignement est supérieur à ** \_ \_ STDCPP \_ \_ \_ \_ \_ par défaut**, l’implémentation obtient la mémoire à l’aide de `::operator new(size_t, align_val_t)` . De même, la suppression de types suralignés appelle `::operator delete(void*, align_val_t)` ou la signature de suppression dimensionnée `::operator delete(void*, size_t, align_val_t)`.

L’option **/Zc:alignedNew** est disponible uniquement quand [/std:c++17](std-specify-language-standard-version.md) ou [/std:c++latest](std-specify-language-standard-version.md) est activé. Sous **/std:c++17** ou **/std:c++latest**, **/Zc:alignedNew** est activé par défaut pour être conforme à la norme ISO C++17 standard. Si la seule raison pour laquelle vous implémentez l’opérateur **`new`** et **`delete`** est de prendre en charge des allocations sur-alignées, vous n’avez plus besoin de ce code en mode c++ 17. Pour désactiver cette option et revenir au comportement C++ 14 de **`new`** et **`delete`** quand vous utilisez **/std :: c++ 17** ou **/std : C + + latest**, spécifiez **/Zc : alignedNew-**. Si vous implémentez **`new`** l’opérateur et que **`delete`** vous n’êtes pas prêt à implémenter l’opérateur sur-aligné **`new`** et les **`delete`** surcharges qui ont le `align_val_t` paramètre, utilisez l’option **/Zc : alignedNew-** pour empêcher le compilateur et la bibliothèque standard de générer des appels aux surcharges sur-alignées. L’option [/permissive-](permissive-standards-conformance.md) ne change pas le paramètre par défaut de **/Zc:alignedNew**.

La prise en charge de **/Zc:alignedNew** est disponible à partir de Visual Studio 2017 version 15.5.

## <a name="example"></a>Exemple

Cet exemple montre comment **`new`** l’opérateur et **`delete`** l’opérateur se comportent quand l’option **/Zc : alignedNew** est définie.

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

Cette sortie est généralement pour les builds 32 bits. Les valeurs de pointeur varient selon l’endroit où votre application s’exécute dans la mémoire.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Pour des informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **Options supplémentaires** pour inclure **/Zc:alignedNew** ou **/Zc:alignedNew-**, puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
