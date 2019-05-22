---
title: /Zc:alignedNew (allocation de types suralignés C++17)
ms.date: 05/18/2019
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: dfcc4982e1b5f67b5a01d5a0d09d4fd9279deacf
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934187"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (allocation de types suralignés C++17)

Activez la prise en charge de la **nouvelle** allocation de mémoire dynamique suralignée C++17, alignée sur les limites supérieures à la valeur par défaut de la taille maximale des types alignés standard, **max\_align\_t**.

## <a name="syntax"></a>Syntaxe

> **/Zc:alignedNew**\[-]

## <a name="remarks"></a>Remarques

La bibliothèque et le compilateur MSVC prennent en charge l’allocation de mémoire dynamique suralignée standard C++17. Quand l’option **/Zc:alignedNew** est spécifiée, une allocation dynamique comme `new Example;` respecte l’alignement de *Exemple* même s’il est supérieur à `max_align_t`, le plus grand alignement requis pour tous les types fondamentaux. Lorsque l’alignement du type alloué ne dépasse pas l’alignement garanti par l’opérateur d’origine **new**, disponible en tant que valeur de la macro prédéfinie  **\_\_STDCPP\_DEFAULT\_NEW\_ALIGNMENT\_\_**, l’instruction `new Example;` aboutit à un appel à `::operator new(size_t)` comme elle le faisait dans C++14. Lorsque l’alignement est supérieur à **\_\_STDCPP\_DEFAULT\_NEW\_ALIGNMENT\_\_**, l’implémentation obtient la mémoire en utilisant `::operator new(size_t, align_val_t)` à la place. De même, la suppression de types suralignés appelle `::operator delete(void*, align_val_t)` ou la signature de suppression dimensionnée `::operator delete(void*, size_t, align_val_t)`.

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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour des informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++** > **Ligne de commande**.

1. Modifiez la propriété **Options supplémentaires** pour inclure **/Zc:alignedNew** ou **/Zc:alignedNew-**, puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
