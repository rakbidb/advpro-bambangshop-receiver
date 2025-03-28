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
    -   [✅] Commit: `Implement list_messages function in Notification service.`
    -   [✅] Commit: `Implement list function in Notification controller.`
    -   [✅] Write answers of your learning module's "Reflection Subscriber-2" questions in this README.

## Your Reflections
This is the place for you to write reflections:

### Mandatory (Subscriber) Reflections

#### Reflection Subscriber-1

1. In this tutorial, we used RwLock<> to synchronise the use of Vec of Notifications. Explain why it is necessary for this case, and explain why we do not use Mutex<> instead?

    According to the docs, RwLock or Reader-Writer Lock distinguishes the readers and the writer. RwLock allows a number of readers and at most a writer to access the lock. Meanwhile, Mutex won't allow anyone else to access a lock if it's being used by a thread because it doesn't care who is accessing the lock. Therefore, any other threads are blocked if a thread is accessing the mutex. In BambangShop case, RwLock is necessary to support multithreading because there will be a lot of Subscribers that needs to access the database. By using RwLock, every reader are given access to RwLock.

2. In this tutorial, we used lazy_static external library to define Vec and DashMap as a “static” variable. Compared to Java where we can mutate the content of a static variable via a static function, why did not Rust allow us to do so?

    By default, static variables in Rust are immutable. lazy_static prevents direct mutation within the code. This is due to safety concerns. By making static variables immutable, Rust provides a thread-safe and more predictable code. Java allows mutation of content of static variable. However, this can lead to data races if not handled carefully.

#### Reflection Subscriber-2

1. Have you explored things outside of the steps in the tutorial, for example: src/lib.rs? If not, explain why you did not do so. If yes, explain things that you have learned from those other parts of code.

    From what I have read, we set up our app config in lib.rs (kinda like settings.py in Django). There, we set the configurations like APP_NAME or ROOT_URL (things we put in .env file) and the prefixes/default values (if there's any). We can also define a custom error message there. We also set up the singletons there.

2. Since you have completed the tutorial by now and have tried to test your notification system by spawning multiple instances of Receiver, explain how Observer pattern eases you to plug in more subscribers. How about spawning more than one instance of Main app, will it still be easy enough to add to the system?

    Using Observer pattern eased me on adding more subscriber to the system. Whenever there's a new subscriber, they will be added to the list of subscriber on the main app. If a situation similar to the one described in the question arises, where an occurrence of the Main app is created, there shouldn't be any issue as it simply requires adapting the process of adding subscribers to the suitable API.

3. Have you tried to make your own Tests, or enhance documentation on your Postman collection? If you have tried those features, tell us whether it is useful for your work (it can be your tutorial work or your Group Project).

    I have tried making my own test. Testing with Postman collection is quite easy and helpful.  We have the ability to modify the data sent in the HTTP request and then verify whether the expected response from our program is accurate.