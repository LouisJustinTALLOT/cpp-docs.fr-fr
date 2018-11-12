---
title: /Zc:alignedNew (c ++ 17 suralignés allocation)
ms.date: 02/28/2018
f1_keywords:
- /Zc:alignedNew
helpviewer_keywords:
- /Zc:alignedNew
- Zc:alignedNew
- -Zc:alignedNew
ms.openlocfilehash: 0e6cf408e56dd6e5bc262c39dda460253a32dfc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662460"
---
# <a name="zcalignednew-c17-over-aligned-allocation"></a>/Zc:alignedNew (c ++ 17 suralignés allocation)

Activer la prise en charge de C ++ 17 sur-alignés **nouveau**, allocation de mémoire dynamique alignée sur les limites supérieures à la valeur par défaut pour la taille maximale standard type aligné, **max\_aligner\_t**.

## <a name="syntax"></a>Syntaxe

> **/Zc:alignedNew**[-]

## <a name="remarks"></a>Notes

Visual Studio version 15.5 permet de compilateur et prise en charge de la bibliothèque de C ++ 17 standard suralignés allocation de mémoire dynamique. Lorsque le **/Zc:alignedNew** option est spécifiée, une allocation dynamique comme `new Example;` respecte l’alignement de *exemple* même si elle est supérieure à `max_align_t`, le plus grand alignement obligatoire pour n’importe quel type fondamental. Lorsque l’alignement du type alloué ne dépasse pas assuré par l’opérateur d’origine **nouveau**, disponible en tant que la valeur de la macro prédéfinie  **\_ \_STDCPP\_par défaut \_NEW\_alignement\_\_**, l’instruction `new Example;` entraîne un appel à `::operator new(size_t)` comme elle le faisait dans C ++ 14. Lorsque l’alignement est supérieur à  **\_ \_STDCPP\_par défaut\_NEW\_alignement\_\_**, l’implémentation obtient à la place la mémoire à l’aide de `::operator new(size_t, align_val_t)`. De même, la suppression de types suralignés appelle `::operator delete(void*, align_val_t)` ou la taille supprimer signature `::operator delete(void*, size_t, align_val_t)`.

Le **/Zc:alignedNew** option est disponible uniquement lorsque [/std : c ++ 17](std-specify-language-standard-version.md) ou [/std : c ++ dernière](std-specify-language-standard-version.md) est activé. Sous **/std : c ++ 17** ou **/std : c ++ dernière**, **/Zc:alignedNew** est activée par défaut pour être conforme à la norme ISO C ++ 17 standard. Si la seule raison vous implémenter opérateur **nouveau** et **supprimer** doit prendre en charge les allocations suralignées, vous devrez peut-être n’est plus ce code en mode C ++ 17. Pour désactiver cette option et revenir à l’interface C ++ 14 de **nouveau** et **supprimer** lorsque **/std::c ++ 17** ou **/std : c ++ dernière** est spécifié, Spécifiez **/Zc:alignedNew-**. Si vous implémentez opérateur **nouveau** et **supprimer** , mais vous n’êtes pas prêt à implémenter l’opérateur suraligné **nouveau** et **supprimer** surcharges ayant le `align_val_t` paramètre, utilisez le **/Zc:alignedNew-** option permettant d’empêcher le compilateur et la bibliothèque Standard à partir de la génération d’appels aux surcharges suralignés. Le [/ permissive-](permissive-standards-conformance.md) option ne change pas le paramètre par défaut **/Zc:alignedNew**.

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

Cette sortie est généralement utilisée pour les versions 32 bits. Le pointeur de valeurs varient selon où votre application s’exécute en mémoire.

```Output
unaligned new(4) = 009FD0D0
unaligned sized delete(009FD0D0, 4)
aligned new(256, 256) = 009FE800
aligned sized delete(009FE800, 256, 256)
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc:alignedNew** ou **/Zc:alignedNew-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)
