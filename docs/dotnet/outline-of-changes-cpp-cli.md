---
title: Plan des modifications (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2a9662f73844013a944fc2b04ce6d3627d4e4b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138299"
---
# <a name="outline-of-changes-ccli"></a>Plan des modifications (C++/CLI)
Ce plan propose des exemples de certaines modifications dans le langage des Extensions managées pour C++ vers Visual C++. Suivez le lien qui accompagne chaque élément pour plus d’informations.  
  
## <a name="no-double-underscore-keywords"></a>Aucun mot clé Double trait de soulignement  
 Le trait de soulignement double devant tous les mots clés a été supprimé, avec une exception. Par conséquent, `__value` devient `value`, et `__interface` devient `interface`, et ainsi de suite. Pour éviter les conflits de nom entre les mots clés et des identificateurs dans le code utilisateur, les mots clés sont essentiellement traités comme contextuels.  
  
 Consultez [mots clés de langage (C + c++ / CLI)](../dotnet/language-keywords-cpp-cli.md) pour plus d’informations.  
  
## <a name="class-declarations"></a>Déclarations de classe  
 Syntaxe des Extensions managées :  
  
```  
__gc class Block {};                           // reference class  
__value class Vector {};                       // value class  
__interface I {};                        // interface class  
__gc __abstract class Shape {};                // abstract class  
__gc __sealed class Shape2D : public Shape {}; // derived class  
```  
  
 Nouvelle syntaxe :  
  
```  
ref class Block {};                // reference class  
value class Vector {};             // value class  
interface class I {};        // interface class  
ref class Shape abstract {};       // abstract class  
ref class Shape2D sealed: Shape{}; // derived class  
```  
  
 Consultez [Managed Types (C + c++ / CL)](../dotnet/managed-types-cpp-cl.md) pour plus d’informations.  
  
## <a name="object-declaration"></a>Déclaration d’objet  
 Syntaxe des Extensions managées :  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   System::Windows::Forms::Button   __gc *button1;  
   System::Windows::Forms::DataGrid __gc *myDataGrid;     
   System::Data::DataSet  __gc *myDataSet;  
};  
```  
  
 Nouvelle syntaxe :  
  
```  
public ref class Form1 : System::Windows::Forms::Form {  
   System::ComponentModel::Container^ components;  
   System::Windows::Forms::Button^ button1;  
   System::Windows::Forms::DataGrid^ myDataGrid;  
   System::Data::DataSet^ myDataSet;  
};  
```  
  
 Consultez [déclaration d’un objet de classe de référence CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) pour plus d’informations.  
  
### <a name="managed-heap-allocation"></a>Allocation de tas managé  
 Syntaxe des Extensions managées :  
  
```  
Button* button1 = new Button; // managed heap  
int *pi1 = new int;           // native heap  
Int32 *pi2 = new Int32;       // managed heap  
```  
  
 Nouvelle syntaxe :  
  
```  
Button^ button1 = gcnew Button;        // managed heap  
int * pi1 = new int;                   // native heap  
Int32^ pi2 = gcnew Int32;              // managed heap  
```  
  
 Consultez [déclaration d’un objet de classe de référence CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) pour plus d’informations.  
  
### <a name="a-tracking-reference-to-no-object"></a>Une référence de suivi à aucun objet  
 Syntaxe des Extensions managées :  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 Nouvelle syntaxe :  
  
```  
// Incorrect Translation  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
  
// Correct Translation  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to an Int32^  
Object ^ obj2 = 1;  
```  
  
 Consultez [déclaration d’un objet de classe de référence CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) pour plus d’informations.  
  
## <a name="array-declaration"></a>Déclaration de tableau  
 Le tableau CLR a été modifié. Il est similaire à la bibliothèque stl `vector` la collection de modèle, mais correspond à sous-jacent `System::Array` classe : autrement dit, il n’est pas une implémentation de modèle.  
  
 Consultez [déclaration d’un tableau CLR](../dotnet/declaration-of-a-clr-array.md) pour plus d’informations.  
  
### <a name="array-as-parameter"></a>Tableau comme paramètre  
 Syntaxe de tableau d’Extensions managées :  
  
```  
void PrintValues( Object* myArr __gc[]);   
void PrintValues( int myArr __gc[,,]);   
```  
  
 Nouvelle syntaxe de tableau :  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
### <a name="array-as-return-type"></a>Tableau en tant que Type de retour  
 Syntaxe de tableau d’Extensions managées :  
  
```  
Int32 f() [];   
int GetArray() __gc[];  
```  
  
 Nouvelle syntaxe de tableau :  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
### <a name="shorthand-initialization-of-local-clr-array"></a>Initialisation abrégée de tableau CLR Local  
 Syntaxe de tableau d’Extensions managées :  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = { __box(26), __box(27), __box(28),  
                                 __box(29), __box(30) };  
  
   return a1;  
}  
```  
  
 Nouvelle syntaxe de tableau :  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
  
   return a1;  
}  
```  
  
### <a name="explicit-clr-array-declaration"></a>Déclaration de tableau CLR explicite  
 Syntaxe de tableau d’Extensions managées :  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 Nouvelle syntaxe de tableau :  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 Nouveauté du langage : initialisation de tableau explicite qui suit gcnew  
  
```  
// explicit initialization list follow gcnew   
// is not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="scalar-properties"></a>Propriétés scalaires  
 Syntaxe de propriété d’Extensions managées :  
  
```  
public __gc __sealed class Vector {  
   double _x;  
  
public:  
   __property double get_x(){ return _x; }  
   __property void set_x( double newx ){ _x = newx; }  
};  
```  
  
 Nouvelle syntaxe de la propriété :  
  
```  
public ref class Vector sealed {   
   double _x;  
  
public:  
   property double x   
   {  
      double get()             { return _x; }  
      void   set( double newx ){ _x = newx; }  
   } // Note: no semi-colon  
};  
```  
  
 Nouveauté du langage : propriétés triviales  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   // backing store is not accessible  
   property double x;   
};  
```  
  
 Consultez [déclaration de propriété](../dotnet/property-declaration.md) pour plus d’informations.  
  
## <a name="indexed-properties"></a>Propriétés indexées  
 Extensions managées indexés la syntaxe de la propriété :  
  
```  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value) { mat[r,c] = value; }  
   __property int get_Item( int r, int c ) { return mat[r,c]; }  
};  
```  
  
 Nouvelle syntaxe de la propriété indexée :  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 Nouveauté du langage : propriété indexée de niveau classe  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //     Matrix mat;  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer  
  
   property float default [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 Consultez [déclaration de propriété d’Index](../dotnet/property-index-declaration.md) pour plus d’informations.  
  
## <a name="overloaded-operators"></a>Opérateurs surchargés  
 Syntaxe de la surcharge d’opérateur Extensions managées :  
  
```  
public __gc __sealed class Vector {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    op_Equality( const Vector*, const Vector* );  
   static Vector* op_Division( const Vector*, double );  
};  
  
int main() {  
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );  
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );   
  
   Vector *pc = Vector::op_Division( pa, 4.8916 );  
  
   if ( Vector::op_Equality( pa, pc ))  
      ;  
}  
```  
  
 Nouvelle syntaxe de la surcharge d’opérateur :  
  
```  
public ref class Vector sealed {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    operator ==( const Vector^, const Vector^ );  
   static Vector^ operator /( const Vector^, double );  
};  
  
int main() {  
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );  
   Vector^ pb = gcnew Vector( 1.475, 4.8916, -1.23 );  
  
   Vector^ pc = pa / 4.8916;  
   if ( pc == pa )  
      ;  
}  
```  
  
 Consultez [opérateurs surchargés](../dotnet/overloaded-operators.md) pour plus d’informations.  
  
## <a name="conversion-operators"></a>Conversion, opérateurs  
 Syntaxe d’opérateur conversion Extensions géré :  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 Nouvelle syntaxe d’opérateur de conversion :  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 Consultez [modifications apportées aux opérateurs de Conversion](../dotnet/changes-to-conversion-operators.md) pour plus d’informations.  
  
## <a name="explicit-override-of-an-interface-member"></a>Substitution explicite d'un membre d'interface  
 Syntaxe de substitution explicite des Extensions managées :  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 Nouvelle syntaxe de substitution explicite :  
  
```  
public ref class R : public ICloneable {  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R   
   virtual R^ Clone();  
};  
```  
  
 Consultez [substitution explicite d’un membre d’Interface](../dotnet/explicit-override-of-an-interface-member.md) pour plus d’informations.  
  
## <a name="private-virtual-functions"></a>Fonctions virtuelles privées  
 Syntaxe de fonction virtuelle privée d’Extensions managées :  
  
```  
__gc class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
__gc class Derived : public Base {  
public:  
   // ok: g() overrides Base::g()  
   virtual void g();  
};  
```  
  
 Nouvelle syntaxe de fonctions virtuelles privées  
  
```  
ref class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
ref class Derived : public Base {  
public:  
   // error: cannot override: Base::g() is inaccessible  
   virtual void g() override;  
};  
```  
  
 Consultez [les fonctions virtuelles privées](../dotnet/private-virtual-functions.md) pour plus d’informations.  
  
## <a name="clr-enum-type"></a>Type Enum du CLR  
 Syntaxe des Extensions managées enum :  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};    
```  
  
 Nouvelle syntaxe enum :  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 Outre cette légère modification syntaxique, le comportement du type d’enum CLR a été modifié de plusieurs façons :  
  
-   Une déclaration anticipée d’un enum du CLR n’est plus pris en charge.  
  
-   La résolution de surcharge entre les types arithmétiques intégrés et la hiérarchie de classes d’objet a été inversée entre Extensions managées et de Visual C++. En effet, les énumérations CLR sont ne sont plus converties implicitement en types arithmétiques.  
  
-   Dans la nouvelle syntaxe, un enum du CLR conserve sa propre portée, ce qui n’est pas le cas dans les Extensions managées. Auparavant, les énumérateurs étaient visibles dans la portée contenant l’enum ; maintenant, les énumérateurs sont encapsulés dans la portée de l’enum.  
  
 Consultez [Enum Type du CLR](../dotnet/clr-enum-type.md) pour plus d’informations.  
  
## <a name="removal-of-box-keyword"></a>Suppression de __box (mot clé)  
 Conversion boxing de syntaxe des Extensions managées :  
  
```  
Object *o = __box( 1024 ); // explicit boxing  
```  
  
 Nouvelle syntaxe de conversion boxing :  
  
```  
Object ^o = 1024; // implicit boxing  
```  
  
 Consultez [suivi descripteur à une valeur Boxed](../dotnet/a-tracking-handle-to-a-boxed-value.md) pour plus d’informations.  
  
## <a name="pinning-pointer"></a>Pointeur épingle  
 Syntaxe du pointeur épingle en Extensions managées :  
  
```  
__gc struct H { int j; };  
  
int main() {  
   H * h = new H;  
   int __pin * k = & h -> j;  
};  
```  
  
 Nouvelle syntaxe du pointeur épingle :  
  
```  
ref struct H { int j; };  
  
int main() {  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
}  
```  
  
 Consultez [une sémantique de Type valeur](../dotnet/value-type-semantics.md) pour plus d’informations.  
  
## <a name="typeof-keyword-becomes-typeid"></a>mot clé __typeof devient typeid  
 Syntaxe de typeof Extensions managées :  
  
```  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 Nouvelle syntaxe de typeid :  
  
```  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
 Consultez [typeof va à T::typeid](../dotnet/typeof-goes-to-t-typeid.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [C + c++ / CLI Initiation à la Migration](../dotnet/cpp-cli-migration-primer.md)   
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)


