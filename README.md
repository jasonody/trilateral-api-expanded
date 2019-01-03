# Trilateral API Expanded

This example includes several Lambda functions, a Kinesis stream and an API Gateway

> This example builds on the implementation of the Trilateral API presented in [Cloud Native Development Patterns and Best Practices](https://github.com/PacktPublishing/Cloud-Native-Development-Patterns-and-Best-Practices/tree/master/Chapter03/trilateral-api)

## Steps
1. Execute: `npm install`
2. Execute: `npm run dp:dev:e`
3. In the AWS console review the various tabs for the following:
   * Cloudformation Stack: `cndp-trilateral-api-dev`
   * Lambda functions: `cndp-trilateral-api-dev-*`
   * API Gateway: `cndp-trilateral-api`
4. Invoke POST api from the API Gateway console by pressing the `Invoke URL` link:
   * APIs > dev-cndp-trilateral-api (...) > Stages > dev > /things > POST
5. Inspect the DynamoDB `dev-cndp-trilateral-api-t1` table for the new contents
   * Copy an `id` for step 6
   * Verify that none of the records are flagged as deleted
6. Inspect the Lambda Monitoring tab and logs for function: `cndp-trilateral-api-dev-publish`
7. Invoke GET api from the API Gateway console by pressing the `Invoke URL` link:
   * APIs > dev-cndp-trilateral-api (...) > Stages > dev > /things/{id} > GET
8. Inspect the Lambda Monitoring tab and logs for function: `cndp-trilateral-api-dev-query`
9. Invoke Lambda function `cndp-trilateral-api-dev-produce-category-deleted` from the AWS console by pressing the Test button
   * Accept the defaults if asked.
10. Inspect the Lambda Monitoring tab and logs for function: `cndp-trilateral-api-dev-subscribe`
11. Inspect the DynamoDB `dev-cndp-trilateral-api-t1` table for the new updates
    * Verify that the records with the "widgets" category are flagged as deleted
12. Execute: `npm run rm:dev:e`
