---
title: Double Thunking (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 47d5bbbecc8e1b9743c543a503df1a0afa0dc0ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111206"
---
# <a name="double-thunking-c"></a>Double conversion de code (thunking) (C++)
Double médiateur fait référence à la perte de performances que peuvent se produire lorsqu’un appel de fonction dans un contexte managé appelle une Visual C++ fonction managée et où l’exécution du programme appelle le point d’entrée natif de la fonction afin d’appeler la fonction managée. Cette rubrique traite des cas de double médiateur et comment vous pouvez l’éviter pour améliorer les performances.  
  
## <a name="remarks"></a>Notes  
 Par défaut, lors de la compilation avec **/CLR**, la définition d’une fonction managée, le compilateur générer un point d’entrée managé et un point d’entrée natif. Ainsi, la fonction managée à être appelée à partir des sites d’appel natif et managé. Toutefois, lorsqu’un point d’entrée natif existe, il peut être le point d’entrée pour tous les appels à la fonction. Si une fonction appelante est gérée, le point d’entrée natif appellera ensuite le point d’entrée managé. En effet, les deux appels sont requis pour appeler la fonction (d'où le double médiateur). Par exemple, les fonctions virtuelles sont toujours appelées via un point d’entrée natif.  
  
 Une solution consiste à indiquer au compilateur de ne pas générer de point d’entrée natif pour une fonction managée et que la fonction est uniquement appelée à partir d’un contexte managé, à l’aide de la [__clrcall](../cpp/clrcall.md) convention d’appel.  
  
 De même, si vous exportez ([dllexport, dllimport](../cpp/dllexport-dllimport.md)) une fonction managée, un point d’entrée natif est généré et toute fonction qui importe et appelle cette fonction appellera via le point d’entrée natif. Pour éviter un double médiateur dans cette situation, n’utilisez pas de sémantique d’exportation/importation native ; référencez simplement les métadonnées via `#using` (consultez [#using, Directive](../preprocessor/hash-using-directive-cpp.md)).  
  
 Le compilateur a été mis à jour afin de réduire thunking double inutiles. Par exemple, toute fonction ayant un type managé dans la signature (y compris le type de retour) sera marquée implicitement comme `__clrcall`. Pour plus d’informations sur l’élimination de double conversion de code, consultez [ http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx ](http://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant illustre un double médiateur. Lors de la compilation native (sans **/CLR**), l’appel à la fonction virtuelle dans `main` génère un appel à `T`du constructeur de copie et un appel au destructeur. Un comportement similaire survient lorsque la fonction virtuelle est déclarée avec **/CLR** et `__clrcall`. Toutefois, lors de la compilation juste avec **/CLR**, l’appel de fonction génère un appel au constructeur de copie, mais il existe un autre appel au constructeur de copie en raison de la conversion de code natif et managé.  
  
### <a name="code"></a>Code  
  
```  
// double_thunking.cpp  
// compile with: /clr  
#include <stdio.h>  
struct T {  
   T() {  
      puts(__FUNCSIG__);  
   }  
  
   T(const T&) {  
      puts(__FUNCSIG__);  
   }  
  
   ~T() {  
      puts(__FUNCSIG__);  
   }  
  
   T& operator=(const T&) {  
      puts(__FUNCSIG__);  
      return *this;  
   }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
  
   printf("calling struct S\n");  
   pS->f(t);  
   printf("after calling struct S\n");  
}  
```  
  
### <a name="sample-output"></a>Résultat de l'exemple  
  
```  
__thiscall T::T(void)  
calling struct S  
__thiscall T::T(const struct T &)  
__thiscall T::T(const struct T &)  
__thiscall T::~T(void)  
__thiscall T::~T(void)  
after calling struct S  
__thiscall T::~T(void)  
```  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple précédent a montré l’existence d’un double médiateur. Cet exemple montre son effet. Le `for` boucle appelle la fonction virtuelle et le programme rapporte le temps d’exécution. Le temps le plus long est signalé lorsque le programme est compilé avec **/CLR**. Les temps le plus rapide sont signalées lors de la compilation sans **/CLR** ou si la fonction virtuelle est déclarée avec `__clrcall`.  
  
### <a name="code"></a>Code  
  
```  
// double_thunking_2.cpp  
// compile with: /clr  
#include <time.h>  
#include <stdio.h>   
  
#pragma unmanaged  
struct T {  
   T() {}  
   T(const T&) {}  
   ~T() {}  
   T& operator=(const T&) { return *this; }  
};  
  
struct S {  
   virtual void /* __clrcall */ f(T t) {};  
} s;  
  
int main() {  
   S* pS = &s;  
   T t;  
   clock_t start, finish;  
   double  duration;  
   start = clock();  
  
   for ( int i = 0 ; i < 1000000 ; i++ )  
      pS->f(t);  
  
   finish = clock();  
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);  
   printf( "%2.1f seconds\n", duration );  
   printf("after calling struct S\n");  
}  
```  
  
### <a name="sample-output"></a>Résultat de l'exemple  
  
```  
4.2 seconds  
after calling struct S  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)