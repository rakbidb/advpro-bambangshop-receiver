# BambangShop Receiver App
Tutorial and Example for Advanced Programming 2024 - Faculty of Computer Science, Universitas Indonesia

---

## Mandatory Checklists (Subscriber)
-   [✅] Clone https://gitlab.com/ichlaffterlalu/bambangshop-receiver to a new repository.
-   **STAGE 1: Implement models and repositories**
    -   [✅] Commit: `Create Notification model struct.`
    -   [✅] Commit: `Create SubscriberRequest model struct.`
    -   [✅] Commit: `Create Notification database and Notification repository struct skeleton.`
    -   [✅] Commit: `Implement add function in Notification repository.`
    -   [✅] Commit: `Implement list_all_as_string function in Notification repository.`
    -   [✅] Write answers of your learning module's "Reflection Subscriber-1" questions in this README.
-   **STAGE 2: Implement services and controllers**
    -   [✅] Commit: `Create Notification service struct skeleton.`
    -   [✅] Commit: `Implement subscribe function in Notification service.`
    -   [✅] Commit: `Implement subscribe function in Notification controller.`
    -   [✅] Commit: `Implement unsubscribe function in Notification service.`
    -   [✅] Commit: `Implement unsubscribe function in Notification controller.`
    -   [✅] Commit: `Implement receive_notification function in Notification service.`
    -   [✅] Commit: `Implement receive function in Notification controller.`
    -   [ ] Commit: `Implement list_messages function in Notification service.`
    -   [ ] Commit: `Implement list function in Notification controller.`
    -   [ ] Write answers of your learning module's "Reflection Subscriber-2" questions in this README.

## Your Reflections
This is the place for you to write reflections:

### Mandatory (Subscriber) Reflections

#### Reflection Subscriber-1

1. In this tutorial, we used RwLock<> to synchronise the use of Vec of Notifications. Explain why it is necessary for this case, and explain why we do not use Mutex<> instead?

    According to the docs, RwLock or Reader-Writer Lock distinguishes the readers and the writer. RwLock allows a number of readers and at most a writer to access the lock. Meanwhile, Mutex won't allow anyone else to access a lock if it's being used by a thread because it doesn't care who is accessing the lock. Therefore, any other threads are blocked if a thread is accessing the mutex. In BambangShop case, RwLock is necessary to support multithreading because there will be a lot of Subscribers that needs to access the database. By using RwLock, every reader are given access to RwLock.

2. In this tutorial, we used lazy_static external library to define Vec and DashMap as a “static” variable. Compared to Java where we can mutate the content of a static variable via a static function, why did not Rust allow us to do so?

    By default, static variables in Rust are immutable. lazy_static prevents direct mutation within the code. This is due to safety concerns. By making static variables immutable, Rust provides a thread-safe and more predictable code. Java allows mutation of content of static variable. However, this can lead to data races if not handled carefully.

#### Reflection Subscriber-2
