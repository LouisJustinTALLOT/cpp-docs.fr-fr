---
title: Erreur du compilateur C2664 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2664
dev_langs:
- C++
helpviewer_keywords:
- C2664
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b35cc8e9935ba476854cce92918def7134198da2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2664"></a>Erreur du compilateur C2664
’fonction’ : impossible de convertir l’argument n de ’type1’ en ’type2’  
  
 Ce problème de conversion de paramètre peut se produire si vous créez une instance d'une classe et si vous essayez d'effectuer une conversion implicite d'un constructeur marqué avec le mot clé `explicit`. Pour plus d’informations sur les conversions explicites, consultez [des Conversions de types définis par l’utilisateur](../../cpp/user-defined-type-conversions-cpp.md).  
  
 Si un objet temporaire est passé à une fonction qui se réfère à un objet en tant que paramètre, cette référence doit être une référence `const`.  
  
 Si un paramètre qui n'est pas du type attendu par la fonction est passé à cette dernière, un objet temporaire est créé à l'aide du constructeur approprié. Cet objet temporaire est ensuite passé à la fonction. Dans ce cas, l'objet temporaire est utilisé pour initialiser la référence. Dans les versions précédentes du langage, toutes les références pouvaient être initialisées par des objets temporaires.  
  
 Pour résoudre l'erreur C2664,  
  
-   Vérifiez à nouveau le prototype de la fonction concernée et corrigez l’argument noté dans le message d’erreur.  
  
-   Prévoyez une conversion explicite si nécessaire.  
  
 L'erreur C2664 peut également être générée si une classe masque un membre dans l'une de ses classes de base.  
  
 Pour plus d’informations, consultez [Comment : convertir System::String en wchar_t * ou char\*](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C2664 et montre comment la corriger.  
  
```  
// C2664.cpp  
// C2664   
struct A {  
   void f(int i) {};  
};  
  
struct B : public A {  
   // To fix, uncomment the following line.  
   // using A::f;  
   void f(A a) {};  
};  
  
int main() {  
   B b;  
   int i = 1;  
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.  
}  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple génère également l'erreur C2664 et montre comment la corriger.  
  
```  
// C2664b.cpp  
// C2664 expected  
struct A {  
   // To fix, uncomment the following line.  
   // A(int i){}  
};  
  
void func( int, A ) {}  
  
int main() {  
   func( 1, 1 );   // No conversion from int to A.  
}  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'erreur C2664 en utilisant un littéral de chaîne pour appeler `Test`, et montre comment la corriger. Le fait que le paramètre soit une référence à `szString` impose qu'un objet soit créé par le constructeur approprié. Le résultat est un objet temporaire qui ne peut pas être utilisé pour initialiser la référence.  
  
```  
// C2664c.cpp  
// compile with: /EHsc  
// C2664 expected  
#include <iostream>  
#include <string.h>  
using namespace std;  
  
class szString {  
   int slen;  
   char *str;  
  
public:  
   szString(const char *);  
   int len() const {   
      return slen;   
   }  
};  
  
// Simple reference cannot bind to temp var.  
void Test(szString &a) {}  
  
// To fix, uncomment the following line.  
// void Test(const szString &a) {}  
  
szString::szString(const char * newstr) : slen(0), str(NULL) {  
   slen=strlen(newstr);  
   str = new char[slen + 1];  
   if (str)  
      strcpy_s(str, (slen + 1), newstr);  
}  
  
int main() {  
   Test("hello");  
}  
```  
  
## <a name="example"></a>Exemple  
 Le compilateur applique désormais les spécifications de la norme C++ pour l'application de `const`. Cet exemple génère l'erreur C2664 :  
  
```  
// C2664d.cpp  
// C2664 expected  
#include <windows.h>  
  
void func1(LPCSTR &s)  
{  
  
}  
  
void func2(LPSTR &s)  
{  
   func1(s);  
}  
  
int main()  
{  
   return 0;  
}  
```  
  
## <a name="example"></a>Exemple  
 Voici une situation plus complexe où l'erreur C2664 est générée, incluant des instructions sur la façon de la corriger :  
  
```  
// C2664e.cpp  
// compile with: /EHsc  
// C2664 expected  
#define _INTL  
#include <locale>  
#include <iostream>  
  
using namespace std;  
#define LEN 90  
  
int main( ) {  
   char* pszExt = "This is the string to be converted!";  
   wchar_t pwszInt [LEN+1];  
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));  
  
   // To fix, delete the following line.  
   char* pszNext;  
  
   // To fix, uncomment the following line.  
   // const char* pszNext;  
  
   wchar_t* pwszNext;  
   mbstate_t state;  
   locale loc("C");    
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
      ( loc ).in( state,  
      pszExt, &pszExt[strlen(pszExt)], pszNext,  
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );  
   // See earlier comment.  
      pwszInt[strlen(pszExt)] = 0;  
   wcout << ( (res!=codecvt_base::error) ?   
                       L"It worked! " : L"It didn't work! " )  
   << L"The converted string is:\n ["  
   << &pwszInt[0]  
   << L"]" << endl;  
  
   exit(-1);  
}  
```  
  
## <a name="example"></a>Exemple  
 Une variable enum n'est pas convertie en son type sous-jacent, de sorte qu'un appel de fonction soit rempli. Pour plus d’informations, consultez [classe enum](../../windows/enum-class-cpp-component-extensions.md). L'exemple suivant génère l'erreur C2664 et montre comment la corriger.  
  
```  
// C2664f.cpp  
// compile with: /clr  
using namespace System;  
public enum class A : Char {  
   None = 0,  
   NonSilent = 1,  
};  
  
void Test(Char c) {}  
  
int main() {  
   A aa = A::None;  
   Test(aa);   // C2664  
   Test(Char(aa));   // OK - fix by using a conversion cast  
}  
```  
  
## <a name="example"></a>Exemple  
 Un bogue dans le compilateur midl entraîne l'émission d'un type wchar_t en tant que type court non signé dans la bibliothèque de types. Pour résoudre cette erreur, effectuez un cast du type dans votre code source C++ ou définissez le type comme une chaîne dans le fichier idl.  
  
```  
// C2664g.idl  
import "prsht.idl";  
  
[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]  
  
interface IMyObj1 : IUnknown {  
   HRESULT  teststr([in, string] wchar_t *wstr);  
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);  
   HRESULT  testbstr([in] BSTR bstr);  
};  
  
[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]  
library myproj1 {  
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]  
   coclass CMyObj1 { interface IMyObj1; };  
}  
```  
  
 L'erreur C2664 est également générée par l'utilisation de `wchar_t` lors du portage du code de Visual C++ 6.0 vers des versions ultérieures. Dans Visual C++ 6.0 et les versions antérieures, `wchar_t` était `typedef` pour `unsigned short`. Il était donc implicitement convertible vers ce type. Après Visual C++ 6.0, `wchar_t` est son propre type intégré, conformément à ce qui est spécifié dans la norme C++. Il n'est plus implicitement convertible vers `unsigned short`. Consultez [/Zc : wchar_t (wchar_t est un Type natif)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant génère l'erreur C2664 et montre comment la corriger.  
  
```  
// C2664h.cpp  
#import "C2664g.tlb"  
using namespace myproj1;  
  
int main() {  
   IMyObj1Ptr ptr;  
  
   wchar_t * mybuff = 0;  
   BSTR bstr = 0;  
   int len;  
   ptr->teststr(mybuff);  
   ptr->testbstr(bstr);  
   ptr->testarr(mybuff, len);   // C2664  
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast  
}  
```  
  
## <a name="example"></a>Exemple  
 L’erreur C2664 peut également se produire si le compilateur ne peut pas déduire les arguments template.  
  
```  
// C2664i.cpp  
#include <stdio.h>  
template <class T, int iType=0>  
class CTypedImg {  
public:  
   CTypedImg() {}  
   void run() {}  
  
   operator CTypedImg<T>& () {  
      return *((CTypedImg<T>*)this);  
    }  
};  
  
template <class t1>  
void test(CTypedImg<t1>& myarg) {  
   myarg.run();  
}  
  
int main() {  
   CTypedImg<float,2> img;  
  
   test((CTypedImg<float>&)img);   // OK  
   test<float>(img);   // OK  
   test(img);   // C2664 - qualify as above to fix  
}  
```