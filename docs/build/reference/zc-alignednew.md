---
title: /Zc:alignedNew (allocation de types suralignés C++17)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 041f62bbbf5f7a2750960d21d1534cf6daf4b874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335687"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (allocation de types suralignés C++17)

Activez la prise en charge de la **nouvelle** allocation de mémoire dynamique suralignée C++17, alignée sur les limites supérieures à la valeur par défaut de la taille maximale des types alignés standard, **max\_align\_t**.

## <a name="syntax"></a>Syntaxe

> **/Zc:alignéNew**\[-]

## <a name="remarks"></a>Notes

La bibliothèque et le compilateur MSVC prennent en charge l’allocation de mémoire dynamique suralignée standard C++17. Lorsque l’option **/Zc:alignéeNew est spécifiée,** une allocation dynamique telle que `new Example;` respecte `max_align_t`l’alignement de *l’exemple,* même quand il est plus grand que , le plus grand alignement requis pour n’importe quel type fondamental. Lorsque l’alignement du type alloué n’est rien de plus que l’alignement garanti par l’opérateur d’origine **nouveau**, disponible `::operator new(size_t)` comme la valeur de la macro prédéfinie ** \_ \_STDCPP\_\_DEFAULT NEW\_ALIGNMENT\_**, l’énoncé `new Example;` se traduit par un appel à comme il l’a fait dans C '14. Lorsque l’alignement est plus `::operator new(size_t, align_val_t)`grand que ** \_ \_STDCPP\_DEFAULT\_NEW\_ALIGNMENT\_**, la mise en œuvre obtient plutôt la mémoire en utilisant . De même, la suppression de types suralignés appelle `::operator delete(void*, align_val_t)` ou la signature de suppression dimensionnée `::operator delete(void*, size_t, align_val_t)`.

L’option **/Zc:alignedNew** est disponible uniquement quand [/std:c++17](std-specify-language-standard-version.md) ou [/std:c++latest](std-specify-language-standard-version.md) est activé. Sous **/std:c++17** ou **/std:c++latest**, **/Zc:alignedNew** est activé par défaut pour être conforme à la norme ISO C++17 standard. Si la seule raison de votre implémentation des opérateurs **new** et **delete** est la prise en charge des allocations suralignées, vous n’aurez peut-être plus besoin de ce code en mode C++17. Pour désactiver cette option et revenir au comportement de C++14 de **new** et **delete** quand vous utilisez **/std::c ++17** ou **/std:c ++latest**, spécifiez **/Zc:alignedNew-**. Si vous implémentez l’opérateur **new** et **delete** alors que vous n’êtes pas prêt à implémenter les surcharges suralignées de l’opérateur **new** et **delete** ayant le paramètre `align_val_t`, utilisez l’option **/Zc:alignedNew-** pour empêcher le compilateur et la bibliothèque Standard de générer des appels aux surcharges suralignées. L’option [/permissive-](permissive-standards-conformance.md) ne change pas le paramètre par défaut de **/Zc:alignedNew**.

La prise en charge de **/Zc:alignedNew** est disponible à partir de Visual Studio 2017 version 15.5.

## <a name="example"></a>Exemple

Cet exemple montre comment l’opérateur **new** et l’opérateur **delete** se comportent quand l’option **/Zc:alignedNew** est définie.

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

1. Sélectionnez la page propriété **Configuration Properties** > **C/CMD** > **Command Line.**

1. Modifiez la propriété **Options supplémentaires** pour inclure **/Zc:alignedNew** ou **/Zc:alignedNew-**, puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
