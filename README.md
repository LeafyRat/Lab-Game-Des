using UnityEngine;

public class bullet : MonoBehaviour
{
    public float speed = 10f;
    public float lifetime = 2f;

    void Start()
    {
        // Destroy bullet after a few seconds
        Destroy(gameObject, lifetime);
    }

    void Update()
    {
        // Move forward every frame
        transform.Translate(Vector2.up * speed * Time.deltaTime);
    }
    void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.CompareTag("Balloon"))
        {
            // Add score
            ScoreManager.instance.AddScore(10);

            // Destroy both
            Destroy(collision.gameObject); // Balloon
            Destroy(gameObject); // Bullet
        }
    }
}
