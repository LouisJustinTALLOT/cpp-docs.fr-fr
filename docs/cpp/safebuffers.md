---
description: 'En savoir plus sur : safebuffers'
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 8fefa12ffcbd81d58f4f5002e27751f03d7c1cb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319350"
---
# <a name="safebuffers"></a>safebuffers

**Spécifique à Microsoft**

Indique au compilateur de ne pas insérer de vérifications de sécurité de dépassement de mémoire tampon pour une fonction.

## <a name="syntax"></a>Syntaxe

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Notes

L’option de compilateur **/GS** force le compilateur à tester les dépassements de mémoire tampon en insérant des vérifications de sécurité sur la pile. Les types de structures de données éligibles pour les vérifications de sécurité sont décrits dans [/GS (vérification de la sécurité de la mémoire tampon)](../build/reference/gs-buffer-security-check.md). Pour plus d’informations sur la détection du dépassement de mémoire tampon, consultez [fonctionnalités de sécurité dans MSVC](https://devblogs.microsoft.com/cppblog/security-features-in-microsoft-visual-c/).

Une révision manuelle du code par un expert ou une analyse externe peut déterminer qu'une fonction est protégée contre un dépassement de mémoire tampon. Dans ce cas, vous pouvez supprimer les vérifications de sécurité pour une fonction en appliquant le **`__declspec(safebuffers)`** mot clé à la déclaration de fonction.

> [!CAUTION]
> Les vérifications de sécurité de la mémoire tampon assurent une protection importante et ont un impact négligeable sur les performances. Par conséquent, nous vous recommandons de ne pas les supprimer, sauf dans la rare éventualité où les performances d'une fonction est un problème critique et où la fonction est réputée pour être sécurisée.

## <a name="inline-functions"></a>Fonctions inline

Une *fonction principale* peut utiliser un mot clé [inline](inline-functions-cpp.md) pour insérer une copie d’une *fonction secondaire*. Si le **`__declspec(safebuffers)`** mot clé est appliqué à une fonction, la détection de dépassement de mémoire tampon est supprimée pour cette fonction. Toutefois, l’incorporation affecte le **`__declspec(safebuffers)`** mot clé des manières suivantes.

Supposons que l’option de compilateur **/GS** soit spécifiée pour les deux fonctions, mais que la fonction principale spécifie le **`__declspec(safebuffers)`** mot clé. Les structures de données présentes dans la fonction secondaire lui permettent de faire l'objet de vérifications de sécurité, et la fonction ne supprime pas ces vérifications. Dans ce cas :

- Spécifiez le mot clé [__forceinline](inline-functions-cpp.md) sur la fonction secondaire pour forcer le compilateur à incorporer cette fonction indépendamment des optimisations du compilateur.

- Étant donné que la fonction secondaire est éligible pour les vérifications de sécurité, les vérifications de sécurité sont également appliquées à la fonction principale même si elle spécifie le **`__declspec(safebuffers)`** mot clé.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser le **`__declspec(safebuffers)`** mot clé.

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Inline, __inline, \_ _forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
