---
title: safebuffers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce106727fac6b3b9903a53fae64bee94441aa038
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685074"
---
# <a name="safebuffers"></a>safebuffers
**Section spécifique à Microsoft**  
  
 Indique au compilateur de ne pas insérer de vérifications de sécurité de dépassement de mémoire tampon pour une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec( safebuffers )  
```  
  
## <a name="remarks"></a>Notes  
 Le **/GS** option du compilateur indique au compilateur de test pour les dépassements de mémoire tampon en insérant des vérifications de sécurité sur la pile. Les types de structures de données qui sont éligibles pour les vérifications de sécurité sont décrits dans [/GS (vérification de la sécurité de la mémoire tampon)](../build/reference/gs-buffer-security-check.md). Pour plus d’informations sur la détection de dépassement de mémoire tampon, consultez [fonctionnalités de sécurité dans MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).  
  
 Une revue manuelle du code par un expert ou une analyse externe peut déterminer qu’une fonction est protégée contre un dépassement de mémoire tampon. Dans ce cas, vous pouvez supprimer les vérifications de sécurité pour une fonction en appliquant la **__declspec (safebuffers)** mot clé à la déclaration de fonction.  
  
> [!CAUTION]
>  Les vérifications de sécurité de la mémoire tampon assurent une protection importante et ont un impact négligeable sur les performances. Par conséquent, nous vous recommandons de ne pas les supprimer, sauf dans la rare éventualité où les performances d'une fonction est un problème critique et où la fonction est réputée pour être sécurisée.  
  
## <a name="inline-functions"></a>Fonctions inline  
 A *fonction principale* peut utiliser un [incorporation (inlining)](inline-functions-cpp.md) mot clé pour insérer une copie d’un *fonction secondaire*. Si le **__declspec (safebuffers)** mot clé est appliqué à une fonction, la détection de dépassement de mémoire tampon est supprimée pour cette fonction. Toutefois, incorporation affecte le **__declspec (safebuffers)** mot clé comme suit.  
  
 Supposons que le **/GS** option du compilateur est spécifiée pour les deux fonctions, mais la fonction principale Spécifie le **__declspec (safebuffers)** mot clé. Les structures de données présentes dans la fonction secondaire lui permettent de faire l'objet de vérifications de sécurité, et la fonction ne supprime pas ces vérifications. Dans ce cas :  
  
-   Spécifiez le [__forceinline](inline-functions-cpp.md) mot clé dans la fonction secondaire pour forcer le compilateur à incorporer cette fonction indépendamment des optimisations du compilateur.  
  
-   Étant donné que la fonction secondaire est éligible pour les vérifications de sécurité, vérifications de sécurité sont également appliquées à la fonction principale même si elle spécifie le **__declspec (safebuffers)** mot clé.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment utiliser le **__declspec (safebuffers)** mot clé.  
  
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
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__declspec](../cpp/declspec.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [inline, __inline, \__forceinline](inline-functions-cpp.md)   
 [strict_gs_check](../preprocessor/strict-gs-check.md)