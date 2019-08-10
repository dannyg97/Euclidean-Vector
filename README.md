# Euclidean Vector
A full C++ implementation of a Euclidean Vector library class, with interface *euclidean_vector.h* and it's corresponding implementation in *euclidean_vector.cpp*.

**Constructors**

| Name | Constructor | Description | Example |
|----|----|----|----|
| Default Constructor | ```EuclideanVector(int)``` | A constructor that takes the number of dimensions (as a int) but no magnitudes, sets the magnitude in each dimension as 0.0. This is the default constructor, with the default value being 1. | ```EuclideanVector a{1}``` |
| Constructor | ```EuclideanVector(int, double)``` | 	A constructor that takes the number of dimensions (as a int) and initialises the magnitude in each dimension as the second argument (a double). | ```EuclideanVector a{2, 4.0};``` |
| Constructor | ```EuclideanVector(const_iterator, const_iterator)``` | A constructor (or constructors) that takes the start and end of an iterator to a std:vector and works out the required dimensions, and sets the magnitude in each dimension according to the iterated values. | ```std::vector<double> v;  EuclideanVector b{v.begin(),v.end()};``` |
| Copy Constructor | ```EuclideanVector(const EuclideanVector&)``` | A constructor that copies an existing EuclideanVector | ```EuclideanVector aCopy{a};``` |
| Move Constructor | ```EuclideanVector(EuclideanVector&&)``` | A constructor that moves an existing EuclideanVector; the moved EuclideanVector has it's size and contents destroyed and zeroed out. | ```EuclideanVector aMove{std::move(a)}``` |

**Destructors**

This library uses the default destructors.

**Operations**

| Name | Operator | Description | Example |
|----|----|----|----|
| Copy Assignment | ```EuclideanVector& operator=(const EuclideanVector&)``` | A copy assignment operator overload | ```a = b;``` |
| Move Assignment | ```EuclideanVector& operator=(EuclideanVector&&)``` | A move assignment operator | ```a = std::move(b);``` |
| Subscript | ```operator[]``` | Allows to get and set the value in a given dimension of the Euclidean Vector. Const and non-const versions of this function exist. | ```double a {b[1]};``` |
| Addition | ```EuclideanVector& operator+=(const EuclideanVector&)``` | For adding vectors of the same dimension. | ```a += b;``` |
| Subtraction | ```EuclideanVector& operator-=(const EuclideanVector&)``` | For subtracting vectors of the same dimension. | ```a -= b;``` |
| Multiplication | ```EuclideanVector& operator*=(double)``` | For scalar multiplication, e.g. [1 2] * 3 = [3 6] | ```a *= 3;``` |
| Division | ```EuclideanVector& operator/=(double)``` | For scalar division, e.g. [3 6] / 2 = [1.5 3] | ```a /= 4;``` |
| Vector Type Conversion | ```explicit operator std::vector<double>()``` | Operators for type casting to a std::vector | ```auto vf = std::vector<double>{a};``` |
| List Type Conversion | ```explicit operator std::list<double>()``` | Operators for type casting to a std::list | ```auto lf = std::list<double>{a};``` |

**Methods**

| Method | Description | Example |
|----|----|----|
| ```double at(int) const``` | Returns the value of the magnitude in the dimension given as the function parameter | ```a.at(1);``` |
| ```double& at(int)``` | Returns the reference of the magnitude in the dimension given as the function parameter | ```a.at(1);``` |
| ```int GetNumDimensions()``` | Return the number of dimensions in a particular EuclideanVector | ```a.GetNumDimensions();``` |
| ```double GetEuclideanNorm()``` | Returns the Euclidean norm of the vector as a double. The Euclidean norm is the square root of the sum of the squares of the magnitudes in each dimension. E.g, for the vector [1 2 3] the Euclidean norm is ```sqrt(1*1 + 2*2 + 3*3) = 3.74.``` | ```a.GetEuclideanNorm();``` |
| ```EuclideanVector CreateUnitVector()``` | Returns a Euclidean vector that is the unit vector of the current vector. The magnitude for each dimension in the unit vector is the original vector's magnitude divided by the Euclidean norm. | ```a.CreateUnitVector();``` |

**Friends**

| Name | Operator | Description | Example |
|----|----|----|----|
| Equal | ```	bool operator==(const EuclideanVector&, const EuclideanVector&)``` | True if the two vectors are equal in the number of dimensions and the magnitude in each dimension is equal. | ```a == b;``` |
| Not Equal | ```	bool operator!=(const EuclideanVector&, const EuclideanVector&)``` | True if the two vectors are not equal in the number of dimensions or the magnitude in each dimension is not equal. | ```a != b;``` |
| Addition | ```EuclideanVector operator+(const EuclideanVector&, const EuclideanVector&)``` | For adding vectors of the same dimension. | ```a = b + c;``` |
| Subtraction | ```EuclideanVector operator-(const EuclideanVector&, const EuclideanVector&)``` | For subtracting vectors of the same dimension. | ```a = b - c;``` |
| Multiplication | ```double operator*(const EuclideanVector&, const EuclideanVector&)``` | For dot-product multiplication, returns a double. E.g., [1 2] * [3 4] = 1 * 3 + 2 * 4 = 11 | ```double c {a * b};``` |
| Multiplication | ```	EuclideanVector operator*(const EuclideanVector&, double)``` | For scalar multiplication, e.g. [1 2] * 3 = 3 * [1 2] = [3 6]. Works on either side. | ```a = b * 3;``` |
| Division | ```EuclideanVector operator/(const EuclideanVector&, double)``` | For scalar division, e.g. [3 6] / 2 = [1.5 3] | ```EuclideanVector a = b / c;``` |
| List Type Conversion | ```std::ostream& operator<<(std::ostream&, const EuclideanVector&)``` | Prints out the magnitude in each dimension of the Euclidean Vector (surrounded by [ and ]), e.g. for a 3-dimensional vector: [1 2 3] | ```std::cout << a;``` |

**Internal Representation**

The Euclidean Vector stores the magnitudes of each dimension inside of a unique_ptr to a C-style double array and thus does not require any (direct) use of the new/malloc call.

*Created as an assignment from UNSW's Advanced C++ Programming course*
