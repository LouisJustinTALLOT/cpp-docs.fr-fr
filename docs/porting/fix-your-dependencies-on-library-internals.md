---
title: Résoudre vos dépendances aux éléments internes de bibliothèque
ms.date: 05/24/2017
helpviewer_keywords:
- library internals in an upgraded Visual Studio C++ project
- _Hash_seq in an upgraded Visual Studio C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
ms.openlocfilehash: af395ea6f8c8e6a88bd2b003f0eee948bde8b6a9
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449103"
---
# <a name="fix-your-dependencies-on-library-internals"></a>Résoudre vos dépendances aux éléments internes de bibliothèque

Microsoft a publié le code source de la bibliothèque standard, la majeure partie de la bibliothèque Runtime C ainsi que d’autres bibliothèques Microsoft de nombreuses versions de Visual Studio. L’objectif est de vous aider à comprendre le comportement de la bibliothèque pour que vous puissiez déboguer votre code. Un effet secondaire de la publication du code source de la bibliothèque fait que même si elles ne font pas partie de l’interface de la bibliothèque, certaines structures de données, fonctions et valeurs internes sont exposées. Celles-ci portent généralement un nom commençant par deux traits de soulignement, ou un trait de soulignement suivi d’une lettre majuscule, des noms que la norme C++ réserve aux implémentations. Ces valeurs, structures et fonctions sont des détails d’implémentation susceptibles de changer au fur et à mesure que les bibliothèques évoluent au fil du temps, c’est pourquoi nous vous déconseillons fortement de prendre des dépendances à elles. Si vous le faites, vous risquez d’avoir des problèmes et d’obtenir un code non portable lorsque vous tenterez de migrer votre code vers les nouvelles versions des bibliothèques.

Dans la plupart des cas, la documentation sur les nouveautés ou les changements importants de chaque version de Visual Studio ne mentionne pas les modifications apportées aux éléments internes des bibliothèques. De toute façon, ces détails d’implémentation ne sont pas censés avoir une quelconque incidence pour vous. Toutefois, il est parfois très tentant d’utiliser le code qui est visible dans la bibliothèque. Cette rubrique décrit les dépendances à des éléments internes de la bibliothèque standard ou CRT sur lesquels vous avez pu vous appuyer, ainsi que la manière de mettre à jour votre code pour supprimer ces dépendances et le rendre plus portable, ou de migrer vers de nouvelles versions de la bibliothèque.

## <a name="hashseq"></a>_Hash_seq

La fonction de hachage interne `std::_Hash_seq(const unsigned char *, size_t)`, utilisée pour implémenter `std::hash` dans certains types de chaînes, était visible dans les versions récentes de la bibliothèque standard. Cette fonction implémentait un [hachage FNV-1a]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) dans une séquence de caractères.

Pour supprimer cette dépendance, vous avez deux possibilités.

- Si votre objectif est de placer une séquence `const char *` dans un conteneur non ordonné à l’aide de la même machine de code de hachage que `basic_string`, vous pouvez le faire à l’aide de la surcharge de modèle `std::hash` qui prend un `std::string_view`, ce qui retourne le code de hachage sous une forme portable. Il est possible qu’à l’avenir le code de bibliothèque de chaîne s’appuie ou non sur l’utilisation d’une fonction de hachage FNV-1a, ceci est donc la meilleure façon d’éviter la dépendance à un algorithme de hachage particulier.

- Si votre objectif est de générer un algorithme de hachage FNV-1a par rapport à une mémoire arbitraire, ce code est mis à disposition sur GitHub, dans le dépôt [VCSamples]( https://github.com/Microsoft/vcsamples) du fichier d’en-tête autonome [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq), sous une [licence MIT](https://github.com/Microsoft/VCSamples/blob/master/license.txt). Nous avons également inclus un exemplaire de ce code ici, à toutes fins utiles. Vous pouvez copier ce code dans un fichier d’en-tête, ajouter l’en-tête à n’importe quel code affecté, puis rechercher et remplacer `_Hash_seq` par `fnv1a_hash_bytes`. Vous obtenez un comportement identique à l’implémentation interne dans `_Hash_seq`.

```cpp
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved.
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;
#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
    {
        // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
    }
    return (result);
}
```

## <a name="see-also"></a>Voir aussi

[Mise à niveau de projets à partir de versions antérieures de Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Vue d’ensemble des problèmes de mise à niveau potentiels (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Mettre à niveau votre code vers la bibliothèque Universal CRT](upgrade-your-code-to-the-universal-crt.md)