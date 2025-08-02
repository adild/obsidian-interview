## Pessimistic logging
**Pessimistic locking** assumes that **conflicts are likely**, so it **locks** the data at the **time of access**, preventing others from reading or writing until the transaction completes.

🔧 How It Works
When a transaction reads a row with a **pessimistic lock**:
- Other transactions are **blocked** from updating or even reading (depending on lock type).
- The lock is **held until the transaction completes** (either commit or rollback).

 Types of Pessimistic Locks
1. **PESSIMISTIC_READ**:
    - Allows reading.
    - Prevents updates by others.
    - Other transactions **can** read but **cannot** modify.
2. **PESSIMISTIC_WRITE**:
    - Prevents both reading and writing by others.
    - Ensures exclusive access.
3. **PESSIMISTIC_FORCE_INCREMENT**:
    - Like `PESSIMISTIC_WRITE`, but also increments version (used with versioned entities in JPA).

How to Implement Pessimistic Locking in Spring Boot
### 1. **Entity Setup**

Ensure your entity has a primary key and is mapped correctly:
```
@Entity
public class Product {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private int stock;

    // getters and setters
}
```
### 2. **Repository with Pessimistic Lock**

Use JPA's `@Lock` annotation with `LockModeType.PESSIMISTIC_WRITE`:

```
public interface ProductRepository extends JpaRepository<Product, Long> {

    @Lock(LockModeType.PESSIMISTIC_WRITE)
    @Query("SELECT p FROM Product p WHERE p.id = :id")
    Optional<Product> findByIdForUpdate(@Param("id") Long id);
}
```
### 3. **Service Layer with Transaction**

Wrap your logic in a transaction to ensure the lock is held during the operation:
```
@Service
public class ProductService {

    @Autowired
    private ProductRepository productRepository;

    @Transactional
    public void decrementStock(Long productId) {
        Product product = productRepository.findByIdForUpdate(productId)
            .orElseThrow(() -> new RuntimeException("Product not found"));

        if (product.getStock() <= 0) {
            throw new RuntimeException("Out of stock");
        }

        product.setStock(product.getStock() - 1);
        productRepository.save(product);
    }
}
```
