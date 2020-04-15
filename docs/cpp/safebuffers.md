---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: bc4736ce233ce026ecab9ef38ac8379466b5a0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365582"
---
# <a name="safebuffers"></a>safebuffers

**Microsoft Spécifique**

Indique au compilateur de ne pas insérer de vérifications de sécurité de dépassement de mémoire tampon pour une fonction.

## <a name="syntax"></a>Syntaxe

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Notes

**L’option compilateur /GS** provoque le compilateur de tester pour les dépassements de tampon en insérant des contrôles de sécurité sur la pile. Les types de structures de données éligibles aux contrôles de sécurité sont décrits dans [/GS (Buffer Security Check)](../build/reference/gs-buffer-security-check.md). Pour plus d’informations sur la détection des dépassements de mémoire tampon, voir [Les caractéristiques de sécurité dans MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Une révision manuelle du code par un expert ou une analyse externe peut déterminer qu'une fonction est protégée contre un dépassement de mémoire tampon. Dans ce cas, vous pouvez supprimer les contrôles de sécurité pour une fonction en appliquant le mot clé **__declspec (safebuffers)** à la déclaration de fonction.

> [!CAUTION]
> Les vérifications de sécurité de la mémoire tampon assurent une protection importante et ont un impact négligeable sur les performances. Par conséquent, nous vous recommandons de ne pas les supprimer, sauf dans la rare éventualité où les performances d'une fonction est un problème critique et où la fonction est réputée pour être sécurisée.

## <a name="inline-functions"></a>Fonctions inline

Une *fonction principale* peut utiliser un mot clé [d’inlinisation](inline-functions-cpp.md) pour insérer une copie d’une *fonction secondaire*. Si le mot clé **__declspec (safebuffers)** est appliqué à une fonction, la détection des dépassements de mémoire tampon est supprimée pour cette fonction. Cependant, l’inlining affecte le mot clé **__declspec (safebuffers)** de la manière suivante.

Supposons que l’option de compilateur **/GS** soit spécifiée pour les deux fonctions, mais la fonction principale spécifie le mot clé **__declspec (safebuffers).** Les structures de données présentes dans la fonction secondaire lui permettent de faire l'objet de vérifications de sécurité, et la fonction ne supprime pas ces vérifications. Dans ce cas :

- Spécifiez le mot clé [__forceinline](inline-functions-cpp.md) sur la fonction secondaire pour forcer le compilateur à inline cette fonction indépendamment des optimisations compilateur.

- Étant donné que la fonction secondaire est admissible aux contrôles de sécurité, des contrôles de sécurité sont également appliqués à la fonction principale, même si elle spécifie le mot clé **__declspec (safebuffers).**

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser le mot clé **__declspec (safebuffers).**

```cpp
// compile with: /c /GS
typedef struct {
    int x[20];
} BUFFER;
static int checkBuffers() {
    BUFFER cb;
    // Use the buffer...
    return 0;
};
static __declspec(safebuffers)
    int noCheckBuffers() {
    BUFFER ncb;
    // Use the buffer...
    return 0;
}
int wmain() {
    checkBuffers();
    noCheckBuffers();
    return 0;
}
```

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[en ligne, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
