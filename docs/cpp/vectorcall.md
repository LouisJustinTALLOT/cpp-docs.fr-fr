---
title: __vectorcall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c05707f3d6d6e323bf9605c3c742f6bef417d817
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939778"
---
# <a name="vectorcall"></a>__vectorcall
**Section spécifique à Microsoft**  
  
 La convention d'appel `__vectorcall` spécifie que les arguments des fonctions doivent être passés dans les registres, lorsque cela est possible. `__vectorcall` utilise plus de registres pour les arguments que [__fastcall](../cpp/fastcall.md) ou la valeur par défaut [x64 convention d’appel](../build/overview-of-x64-calling-conventions.md) utiliser. La convention d'appel `__vectorcall` est prise en charge uniquement dans le code natif sur les processeurs x86 et x64 qui incluent les extensions Streaming SIMD 2 (SSE2) et versions ultérieures. Utilisez `__vectorcall` pour accélérer les fonctions qui passent plusieurs arguments à virgule flottante ou de type vecteur SIMD, et effectuent des opérations qui tirent parti des arguments chargés dans les registres. La liste ci-dessous indique les fonctionnalités qui sont communes aux implémentations x86 et x64 de `__vectorcall`. Les différences sont expliquées plus loin dans cet article.  
  
|Élément|Implémentation|  
|-------------|--------------------|  
|Convention de décoration de nom C|Deux signes « arobase » (@@) sont ajoutés en suffixe aux noms de fonctions, suivis du nombre d'octets (au format décimal) dans la liste de paramètres.|  
|Convention de conversion de casse|Aucune conversion de casse n'a lieu.|  
  
 À l’aide de la [GV](../build/reference/gd-gr-gv-gz-calling-convention.md) option du compilateur provoque de chaque fonction dans le module pour compiler en `__vectorcall` , sauf si la fonction est une fonction membre, est déclaré avec un attribut de convention d’appel en conflit, utilise un `vararg` variable liste d’arguments, ou a le nom `main`.  
  
 Vous pouvez passer trois types d’arguments par Registre dans `__vectorcall` fonctions : *type entier* valeurs, *type de vecteur* valeurs, et *agrégat de vecteurs homogènes* (HVA ) valeurs.  
  
 Un type entier répond à deux exigences : il tient dans la taille de registre native du processeur (par exemple, 4 octets sur un ordinateur x86 ou 8 octets sur un ordinateur x64) et il peut être converti en un entier de longueur de registre puis reconverti à son état d’origine sans que sa représentation binaire soit modifiée. Par exemple, n’importe quel type qui peut être promu au **int** sur x86 (**longue** sur x64) — par exemple, un **char** ou **court**, ou qui peut être casté en **int** (**longue** sur x64), puis vers son type d’origine sans être modifié est un type entier. Types d’entiers incluent le pointeur, référence, et **struct** ou **union** types de 4 octets (8 octets sur x64) ou moins. Sur x64 plateformes, plus grande **struct** et **union** types sont passés par référence à la mémoire allouée par l’appelant ; sur x86 plateformes, ils sont passés par valeur sur la pile.  
  
 Un type vectoriel est soit un type à virgule flottante, par exemple, un **float** ou **double**, ou un type vecteur SIMD — par exemple, **__m128** ou **__m256**.  
  
 Un type HVA est un type composite comprenant jusqu'à quatre données membres ayant des types vectoriels identiques. Un type HVA doit respecter la même exigence d’alignement que le type vectoriel de ses membres. Il s’agit d’un exemple d’un HVA **struct** définition qui contient trois types vectoriels identiques et alignement de 32 octets :  
  
```cpp  
typedef struct {  
   __m256 x;  
   __m256 y;  
   __m256 z;  
} hva3;    // 3 element HVA type on __m256  
  
```  
  
 Déclarez vos fonctions explicitement avec le mot clé `__vectorcall` dans les fichiers d'en-tête pour permettre à un code compilé séparément de se lier sans erreurs. Les fonctions doivent être prototypées pour utiliser `__vectorcall` et ne peuvent pas utiliser une liste d'arguments de longueur variable `vararg`.  
  
 Une fonction membre peut être déclarée à l'aide du spécificateur `__vectorcall`. Le texte masqué **cela** pointeur est passé par Registre en tant que premier argument de type entier.  
  
 Sur les ordinateurs ARM, `__vectorcall` est accepté et ignoré par le compilateur.  
  
 Pour les fonctions membres de classe non statiques, si la fonction est définie hors ligne, il n'est pas nécessaire de spécifier le modificateur de convention d'appel dans la définition hors ligne. En d'autres termes, pour les membres non statiques d'une classe, la convention d'appel spécifiée pendant la déclaration est prise par défaut au point de définition. Compte tenu de la définition de classe suivante :  
  
```cpp  
struct MyClass {  
   void __vectorcall mymethod();  
};  
```  
  
 le code suivant :  
  
```cpp  
void MyClass::mymethod() { return; }  
```  
  
 équivaut au code :  
  
```cpp  
void __vectorcall MyClass::mymethod() { return; }  
```  
  
 Le modificateur de convention d'appel `__vectorcall` doit être spécifié lorsqu'un pointeur désignant une fonction `__vectorcall` est créé. L’exemple suivant crée un **typedef** pour un pointeur vers un `__vectorcall` fonction qui accepte quatre **double** arguments et retourne un **__m256** valeur :  
  
```cpp  
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);  
```  
  
## <a name="vectorcall-convention-on-x64"></a>Convention __vectorcall sur x64  
 La convention d'appel `__vectorcall` sur x64 étend la convention d'appel x64 standard pour tirer profit de registres supplémentaires. Les arguments de type entier et les arguments de type vectoriel sont mappés aux registres en fonction de leur position dans la liste d’arguments. Les arguments HVA sont alloués aux registres vectoriels inutilisés.  
  
 Si certains des quatre premiers arguments, de gauche à droite, sont des arguments de type entier, ils sont passés dans le registre correspondant à cette position : RCX, RDX, R8 ou R9. Une zone masquée **cela** pointeur est traité comme le premier argument de type entier. Lorsqu’un argument HVA de l’un des quatre premiers arguments ne peut pas être passé dans les registres disponibles, une référence à la mémoire allouée par l’appelant est passée à la place dans le registre de type entier correspondant. Les arguments de type entier après la quatrième position de paramètre sont passés sur la pile.  
  
 Si certains des six premiers arguments, de gauche à droite, sont des arguments de type vectoriel, ils sont passés par valeur dans les registres vectoriels SSE 0 à 5, selon leur position. À virgule flottante et **__m128** types sont passés dans les registres XMM, et **__m256** types sont passés dans YMM inscrit. Cela diffère de la convention d’appel x64 standard, car les types vectoriels sont passés par valeur et non par référence, et des registres supplémentaires sont utilisés. L’espace de pile cachée alloué pour les arguments de type vectoriel est fixé à 8 octets et le [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) option ne s’applique pas. Les arguments de type vectoriel à partir de la septième position de paramètre sont passés sur la pile par référence à la mémoire allouée par l’appelant.  
  
 Une fois que les registres sont allouées pour les arguments vectoriels, les membres de données des arguments HVA sont allouées, dans l’ordre croissant, aux registres vectoriels inutilisés XMM0 à XMM5 (ou YMM0 à YMM5, pour **__m256** types), tant qu’il existe suffisamment de registres disponibles pour l’ensemble. Si un nombre insuffisant de registres sont disponibles, l’argument HVA est passé par référence à la mémoire allouée par l’appelant. L'espace de pile cachée pour un argument HVA est fixé à 8 octets avec un contenu non défini. Les arguments HVA sont assignés aux registres dans l'ordre, de gauche à droite, dans la liste de paramètres, et peuvent être dans n'importe quelle position. Tout argument HVA dans l'une des quatre premières positions d'argument qui n'est pas assigné aux registres vectoriels est passé par référence dans le registre d'entiers correspondant à sa position. Les arguments HVA passés par référence après la quatrième position de paramètre font l’objet d’un push sur la pile.  
  
 Les résultats des fonctions `__vectorcall` sont retournés par valeur dans les registres, si possible. Les résultats de type entier, y compris les structs et les unions de 8 octets ou moins, sont retournés par valeur dans RAX. Les résultats de type vectoriel sont retournés par valeur dans XMM0 ou YMM0, selon la taille. Les résultats HVA comportent chacun un élément de données retourné par valeur dans les registres XMM0:XMM3 ou YMM0:YMM3, selon la taille de l'élément. Les types de résultats qui ne tiennent pas dans les registres correspondants sont retournés par référence à la mémoire allouée par l'appelant.  
  
 La pile est gérée par l'appelant dans l'implémentation x64 de `__vectorcall`. Le code de prologue et d'épilogue de l'appelant alloue et efface la pile pour la fonction appelée. Les arguments font l’objet d’un push sur la pile, de droite à gauche, et l’espace de pile caché est alloué pour les arguments passés dans les registres.  
  
 Exemples :  
  
```cpp  
// crt_vc64.c  
// Build for amd64 with: cl /arch:AVX /W3 /FAs crt_vc64.c  
// This example creates an annotated assembly listing in  
// crt_vc64.asm.  
  
#include <intrin.h>  
#include <xmmintrin.h>  
  
typedef struct {  
   __m128 array[2];  
} hva2;    // 2 element HVA type on __m128  
  
typedef struct {  
   __m256 array[4];  
} hva4;    // 4 element HVA type on __m256  
  
// Example 1: All vectors  
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.  
// Return value in XMM0.  
__m128 __vectorcall   
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {  
   return d;  
}  
  
// Example 2: Mixed int, float and vector parameters  
// Passes a in RCX, b in XMM1, c in R8, d in XMM3, e in YMM4,   
// f in XMM5, g pushed on stack.   
// Return value in YMM0.  
__m256 __vectorcall   
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {  
   return e;  
}  
  
// Example 3: Mixed int and HVA parameters  
// Passes a in RCX, c in R8, d in R9, and e pushed on stack.  
// Passes b by element in [XMM0:XMM1];   
// b's stack shadow area is 8-bytes of undefined value.   
// Return value in XMM0.  
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {  
   return b.array[0];  
}  
  
// Example 4: Discontiguous HVA   
// Passes a in RCX, b in XMM1, d in XMM3, and e is pushed on stack.  
// Passes c by element in [YMM0,YMM2,YMM4,YMM5], discontiguous because  
// vector arguments b and d were allocated first.   
// Shadow area for c is an 8-byte undefined value.  
// Return value in XMM0.  
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {  
   return b;  
}  
  
// Example 5: Multiple HVA arguments  
// Passes a in RCX, c in R8, e pushed on stack.  
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5], each with   
// stack shadow areas of an 8-byte undefined value.  
// Return value in RAX.  
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {  
   return c + e;  
}  
  
// Example 6: HVA argument passed by reference, returned by register  
// Passes a in [XMM0:XMM1], b passed by reference in RDX, c in YMM2,   
// d in [XMM3:XMM4].   
// Register space was insufficient for b, but not for d.  
// Return value in [YMM0:YMM3].  
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {  
   return b;  
}  
  
int __cdecl main( void )  
{  
   hva4 h4;  
   hva2 h2;  
   int i;  
   float f;  
   __m128 a, b, d;  
   __m256 c, e;  
  
   a = b = d = _mm_set1_ps(3.0f);  
   c = e = _mm256_set1_ps(5.0f);  
   h2.array[0] = _mm_set1_ps(6.0f);  
   h4.array[0] = _mm256_set1_ps(7.0f);  
  
   b = example1(a, b, c, d, e);  
   e = example2(1, b, 3, d, e, 6.0f, 7);  
   d = example3(1, h2, 3, 4, 5);  
   f = example4(1, 2.0f, h4, d, 5);  
   i = example5(1, h2, 3, h4, 5);  
   h4 = example6(h2, h4, c, h2);  
}  
  
```  
  
## <a name="vectorcall-convention-on-x86"></a>Convention __vectorcall sur x86  
 Le `__vectorcall` appelant convention suit le **__fastcall** convention pour les arguments de type entier 32 bits et tire profit des registres vectoriels SSE pour le type de vecteur et les arguments HVA.  
  
 Les deux premiers arguments de type entier trouvés dans la liste de paramètres, de gauche à droite, sont placés dans ECX et EDX, respectivement. Une zone masquée **cela** pointeur est traité comme le premier argument de type entier et est passé dans le Registre ECX. Les six premiers arguments de type vecteur sont passés par valeur via les registres vectoriels SSE 0 à 5, dans les registres XMM ou YMM, selon la taille des arguments.  
  
 Les six premiers arguments de type vecteur, dans l’ordre, de gauche à droite, sont passés par valeur dans les registres vectoriels SSE 0 à 5. À virgule flottante et **__m128** types sont passés dans les registres XMM, et **__m256** types sont passés dans YMM inscrit. Aucun espace de pile cachée n’est alloué pour les arguments de type vecteur passés par registre. Le septième argument de type vecteur et les suivants sont passés sur la pile par référence à la mémoire allouée par l’appelant. La limitation de l’erreur du compilateur [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) ne s’applique pas à ces arguments.  
  
 Une fois que les registres sont allouées pour les arguments vectoriels, les données membres des arguments HVA sont allouées dans l’ordre croissant à vectoriels inutilisés registres XMM0 à XMM5 (ou YMM0 à YMM5, pour **__m256** types), tant qu’il existe suffisamment de registres disponibles pour l’ensemble. Si un nombre insuffisant de registres sont disponibles, l’argument HVA est passé sur la pile par référence à la mémoire allouée par l’appelant. Aucun espace de pile cachée n'est alloué pour un argument HVA. Les arguments HVA sont assignés aux registres dans l’ordre, de gauche à droite, dans la liste de paramètres, et peuvent être dans n’importe quelle position.  
  
 Les résultats des fonctions `__vectorcall` sont retournés par valeur dans les registres, si possible. Les résultats de type entier, y compris les structs et les unions de 4 octets ou moins, sont retournés par valeur dans EAX. Les structs et les unions de type entier de 8 octets ou moins sont retournés par valeur dans EDX:EAX. Les résultats de type vectoriel sont retournés par valeur dans XMM0 ou YMM0, selon la taille. Les résultats HVA comportent chacun un élément de données retourné par valeur dans les registres XMM0:XMM3 ou YMM0:YMM3, selon la taille de l'élément. Les autres types de résultats sont retournés par référence à la mémoire allouée par l'appelant.  
  
 L'implémentation x86 de `__vectorcall` suit la convention des arguments faisant l'objet d'un push sur la pile, de droite à gauche, par l'appelant, et la fonction appelée efface la pile juste avant d'être retournée. Seuls les arguments qui ne sont pas placés dans les registres font l’objet d’un push sur la pile.  
  
 Exemples :  
  
```cpp  
// crt_vc86.c  
// Build for x86 with: cl /arch:AVX /W3 /FAs crt_vc86.c  
// This example creates an annotated assembly listing in  
// crt_vc86.asm.  
  
#include <intrin.h>  
#include <xmmintrin.h>  
  
typedef struct {  
   __m128 array[2];  
} hva2;    // 2 element HVA type on __m128  
  
typedef struct {  
   __m256 array[4];  
} hva4;    // 4 element HVA type on __m256  
  
// Example 1: All vectors  
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.  
// Return value in XMM0.  
__m128 __vectorcall   
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {  
   return d;  
}  
  
// Example 2: Mixed int, float and vector parameters  
// Passes a in ECX, b in XMM0, c in EDX, d in XMM1, e in YMM2,   
// f in XMM3, g pushed on stack.   
// Return value in YMM0.  
__m256 __vectorcall   
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {  
   return e;  
}  
  
// Example 3: Mixed int and HVA parameters  
// Passes a in ECX, c in EDX, d and e pushed on stack.  
// Passes b by element in [XMM0:XMM1].   
// Return value in XMM0.  
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {  
   return b.array[0];  
}  
  
// Example 4: HVA assigned after vector types  
// Passes a in ECX, b in XMM0, d in XMM1, and e in EDX.  
// Passes c by element in [YMM2:YMM5].   
// Return value in XMM0.  
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {  
   return b;  
}  
  
// Example 5: Multiple HVA arguments  
// Passes a in ECX, c in EDX, e pushed on stack.  
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5].  
// Return value in EAX.  
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {  
   return c + e;  
}  
  
// Example 6: HVA argument passed by reference, returned by register  
// Passes a in [XMM1:XMM2], b passed by reference in ECX, c in YMM0,   
// d in [XMM3:XMM4].   
// Register space was insufficient for b, but not for d.  
// Return value in [YMM0:YMM3].  
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {  
   return b;  
}  
  
int __cdecl main( void )  
{  
   hva4 h4;  
   hva2 h2;  
   int i;  
   float f;  
   __m128 a, b, d;  
   __m256 c, e;  
  
   a = b = d = _mm_set1_ps(3.0f);  
   c = e = _mm256_set1_ps(5.0f);  
   h2.array[0] = _mm_set1_ps(6.0f);  
   h4.array[0] = _mm256_set1_ps(7.0f);  
  
   b = example1(a, b, c, d, e);  
   e = example2(1, b, 3, d, e, 6.0f, 7);  
   d = example3(1, h2, 3, 4, 5);  
   f = example4(1, 2.0f, h4, d, 5);  
   i = example5(1, h2, 3, h4, 5);  
   h4 = example6(h2, h4, c, h2);  
}  
  
```  
  
 **Fin de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Passage des arguments et Conventions de nommage](../cpp/argument-passing-and-naming-conventions.md)   
 [Mots clés](../cpp/keywords-cpp.md)